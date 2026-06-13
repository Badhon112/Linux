# Kubernetes: Orchestration at Scale

- **What is Kubernetes (K8s)?**
  - K8s is an orchestration tool for deployment, scaling, management of containerize tool for application development.

- **Explain K8s Architecture: API Server, Etcd, Scheduler, Controller Manager**
  - The k8s control plane acts as the central brain of a cluster. relying of for code components to orchestration containers, manages resources, and maintain your system desired state.
  - _API Server_ : The API Server is the front door and communication hub for everything happening inside your k8s Cluster.
  - _ETCD_ : ETCD is the data base that store all configuration data adn the real-time state of every resources
  - _Scheduler_ : The Scheduler is the managing engine that is responsible for assigning your application containers (Pods) to physical or virtual machine (Nodes)
  - _Control Manager_ : The Control manager is the execution and self-healing engine in k8s its run continuous background loops that drive the current state of the cluster toward to desired state

- **What is a ’Pod’? Can a Pod have multiple containers?**
  - A pod is the most common and small deployment unit in k8s. It represent a single instance of a running process in your cluster and acts as a logical host that wrap one or more container.

- **What is a ’ReplicaSet’?**
  - ReplicaSet is the core k8s controller whose primary purpose is to maintain a stable, specific number of pod of identical replica Pods running at any given time

```bash
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
    - name: nginx-pod
      image: nginx
      ports:
        - containerPort: 80
      resources:
        requests:
          cpu: "120Mi"
          memory: "150M"
        limits:
          cpu: "150Mi"
          memory: "200M"

```

- **Explain 'Deployment' vs 'StatefulSet'.**
  - _Deployment_ : Deployment manage the stateless application where all pods are identical and interchangeable. Like web application
  - _StatefulSet_ : StatefulSet manage stateful applications that require unique, persistence identical and dedicated storage. Like database

```bash
# Deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchlabels:
      app: frontend
      role: frontend
  template:
    metadata:
      labels:
        app: frontend
        role: frontend
    spec:
      containers:
        - name: nginx-pod
          image: nginx
          ports:
            - containerPort: 80
          resources:
            requests:
              cpu: "120Mi" # Mebibyte It is a unit of digital memory
              memory: "100M" # M Megabytes . Little m stand for millibytes
            limits:
              cpu: "150Mi"
              memory: "150M"
---
# StatefulSet.yaml
# First Services

apiVersion: v1
kind: Service
metadata:
  name: nginx-svc
spec:
  selector:
    app: frontend
    role: frontend
  ports:
    - port: 80
      targetPort: 80
---
# StateFulSet Config File
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: nginx-sc
spec:
  replicas: 3
  serviceName: nginx-svc
  selector:
    matchLabels:
      app: frontend
      role: frontend
  template:
    metadata:
      labels:
        app: frontend
        role: frontend
    spec:
      containers:
        - name: nginx-pod
          image: nginx
          ports:
            - containerPort: 80
              name: web
          volumeMounts:
            - name: www
              mountPath: /usr/share/nginx/html
    volumeClaimTemplates:
      - metadata:
          name: www
        spec:
          accessModes: ["ReadWriteOnce"]
          resources:
            requests:
              storage: 5Gi

```

- **What is a DaemonSet ?**
  - A DaemonSet is also a workload controller just like deployment but instance of specific a number of pod. DemonSet ensure that the pod will run all the nodes

```bash
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: log-collector
spec:
  selector:
    matchLabels:
      role: frontend
      app: frontend
  template:
    metadata:
      labels:
        role: frontend
        app: frontend
    spec:
      tolerations:
        - key: "node-role.kubernetes.io/control-plane"
          operator: "Exists"
          effect: "NoSchedule"
      containers:
        - name: nginx-pod
          image: nginx
          resources:
            requests:
              cpu: "120Mi"
              memory: "100M"
            limits:
              cpu: "150Mi"
              memory: "150M"
          volumeMounts:
            - name: www
              mountPath: /usr/share/www/html
      volumes:
        - name: www
          hostPath:
            path: /home/badhon

```

- **Explain 'Services' in K8s (ClusterIP, NodePort, LoadBalancer).**
  - In k8s a services is a method for exposing a network application that running as or more pod in the cluster

- **What is an 'Ingress' and 'Ingress Controller' ?**
  - _Ingress_ : An ingress is a k8s resources that defines the rules for external router traffic into your cluster.
  - _Ingress Controller_ : An ingress controller is the actual software component thats reads rules, acts as a reverse proxy.

- ## **Explain 'ConfigMap' and 'Secret' .**
  - _configMap_ : Config map used to store non-confidential key-value configuration data
  - _Secret_ : Secret is specifically for storing sensitive data.

```bash

# ConfigMap.yaml


apiVersion: v1
kind: ConfigMap
metadata:
  name: frontend-cm
data:
  APP: "frontend"
  ENVIRONMENT: "production"

---
apiVersion: v1
kind: Pod
metadata:
  name: myapp
  labels:
    app.kubernetes.io/name: myapp
spec:
  containers:
    - name: nginx
      image: nginx
      resources:
        requests:
          memory: "100Mi"
          cpu: "300m"
        limits:
          memory: "128Mi"
          cpu: "500m"
      ports:
        - containerPort: 80
      env:
        - name: APP
          valueFrom:
            configMapKeyRef:
              name: frontend-cm
              key: APP
        - name: ENVIRONMENT
          valueFrom:
            configMapKeyRef:
              name: frontend-cm
              key: ENVIRONMENT

```

```bash
# secret.yaml
apiVersion: v1
kind: Secret
metadata:
  name: frontend-secret
type: Opaque
data:
  DB_USER: YmFkaG9u             # echo -n "badhon" | base64
  DB_PASSWORD: dGVzdG5ldA==     # echo -n "testnet" | base64
---
apiVersion: v1
kind: Pod
metadata:
  name: myapp
  labels:
    app.kubernetes.io/name: myapp
spec:
  containers:
    - name: nginx
      image: nginx
      resources:
        requests:
          memory: "100Mi"
          cpu: "300m"
        limits:
          memory: "128Mi"
          cpu: "500m"
      ports:
        - containerPort: 80
      env:
        - name: APP
          valueFrom:
            configMapKeyRef:
              name: frontend-secret
              key: DB_USER
        - name: ENVIRONMENT
          valueFrom:
            configMapKeyRef:
              name: frontend-secret
              key: DB_PASSWORD

```

- **What are ’Liveness’, ’Readiness’, and ’Startup’ probes?**
  - k8s liveness, readiness and startup are periodic diagnostic checks used to manage containers health
  - _Liveness_ : Liveness decides when to restart a container .
  - _Readiness_ : Readiness determine if it can handle traffic .
  - _Startup_ : Startup protect slow-starting application .

- **Explain Namespaces.**
  - Namespace provides a virtual partitions inside a single physical cluster that provides logical isolation and resources scopes for different teams. project, or environment.

- **What are Labels and Selectors?**
  - Labels and selectors provides a standard method to group filter items on various criteria
  - 'kubectl get pods --selector app=App1'

- **Explain 'Persistent Volume (PV)' and 'Persistent Volume Claim (PVC)'.**
  - Persistent Volume (PV) : is the actual storage resources provisioned by an administrator,
  - Persistent Volume Claim (PVC): While a PVC is a developers a request for that storage.

- **What is a 'StorageClass' ?**
  - A StorageClass in k8s is an api object that enable dynamic storage provisioning, allowing the cluster to automatically persistence storage volume on demand when an application requests them.

- **Explain ’HPA’ (Horizontal Pod Autoscaler).**
  - HPA is ak8s features that automatically adjusts the number of pod replicas in a deployment or stateful set based on observed resources usage or custom metrics.

```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  selector:
    matchLabels:
      app: frontend
      role: frontend
  template:
    metadata:
      labels:
        app: frontend
        role: frontend
    spec:
      containers:
        - name: nginx-pod
          image: nginx
          resources:
            requests:
              memory: "100Mi"
              cpu: "250m"
            limits:
              memory: "128Mi"
              cpu: "500m"
          ports:
            - containerPort: 80
---

apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: nginx-deployment-as
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: nginx-deployment
  minReplicas: 1
  maxReplicas: 3
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 50


```

- **What is ’VPA’ (Vertical Pod Autoscaler)?**
  - VPA is a k8s automation tool that automatically adjusts the CPU and the memory and CPU requests limits within the workload.

- Explain 'Taints' and 'Tolerations'.
  - Taints and Tolerations are a mechanism that allows you to ensure that pods are not placed in the inappropriate nodes. Taints are added to the nodes and Tolerations are added to the pods.
  - _Taints_ : "kubectl taint nodes nodename special=true:NoSchedule"
  - _Tolerations_ :

  ```bash

  ```
