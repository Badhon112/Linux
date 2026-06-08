## Linux File Operations, Search & Archives

- **Listing Files With LS Command**
  - _ls_ : List files in current directory
  - _ls -l_ : Long format with details (permissions, size, date)
  - _Ls -a_ : Show hidden files (Files starting with .)
  - _ls -lh_ : Human-readable file sizes (KB, MB, GB)
  - _ls -R_ : Recursive listing (show subdirectories)

- **Basic Files Operations**:
  - _touch filename_ : Create empty file or update timestamp
  - _cp source destination_ : Copy files
  - _cp -r folder/ destination/_ : Copy directories recursively
  - _mv source destination_ : Move or rename files
  - _rm filename_ : Delete File (permanent!)
  - _rm -r foldername_ : Delete directory and contents
  - _mkdir foldername_ : Create new directory

- **Finding Files with Find Command**
  - _Finding /path -name "filename"_ : Search by name
  - _find . -name "\*.txt_ : Find all .txt files in current directory
  - _find /var -type f_ : Find only files (not directories)
  - _find /var -type d_ : Find only directories
  - _find . -size +100M_ : Find files large than 100MB
  - _find . -mtime -7_ : Find files modified in last 7 days

- **Searching File Contents with GREP**
  - _Grep "text" filename_ : Search for text in a file
  - _grep -i "error" logfile_ : Case-insensitive search
  - _grep -r "password" /etc_ : Recursive search in directory
  - _grep -n "error" file.log_ : Show line numbers
  - _grep -v "debug" file.log_ : Invert match (exclude lines)
  - _grep -c "error" file.log_ : Count matching lines

- **Creating Archives With Tar**
  - _tar -cvf archive.tar folder/_ : Create tar archive.
  - tar -xvf archive.tar : Extract tar archive
  - tar -czvf archive.tar.gz folder/ : Create compressed tar (grip)\
  - tar -xzvf archive.tar.gz : Extract gzip tar
  - tar -tvf archive.tar : List contents without extracting
  - c = create, x = extract, v = verbose, f = file, z = gzip

- **Compression with GRIP AND ZIP**
  - _GZIP Commands_
    - gzip filename : Compress file (creates filename.gz, removes original)
    - grip -f filename : Compress and keep original file
    - gunzip filename.gz : Decompress grip file
  - _ZIP Commands_
    - zip archive.zip file1 file2 : Create zip archive
    - zip -r archive.zip folder/ : Zip entire directory
    - unzip archive.zip : Extract zip archive
