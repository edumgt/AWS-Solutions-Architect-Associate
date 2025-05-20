
# File Storage
In file storage, data is stored as files in a tree-like hierarchy that consist of folders and subfolders. 
Each file has metadata such as file name, file size, the creation date and a path. 
When you need to retrieve a file, your system can use the path to find it in the file hierarchy.

### Use Case:
Ideal when you require centralized access to files that must be easily shared and managed by multiple host computers.
This storage is typically mounted onto multiple hosts, and requires file locking and integration with existing file system communication protocols.

- Web serving: When the develop a web requires file-level protocols, file naming conventions, and permissions that developers are familiar with
- Analytics: analytics workloads which interact with data through a file interface and rely on features such as file lock or writing to portions of a file.
- Media and entertainment: businesses that use a hybrid cloud deployment and need standardized access using file system protocols (NFS or SMB) or concurrent protocol access
- Home directories: Businesses wanting to take advantage of the scalability and cost benefits of the cloud are extending access to home directories for many of their users.