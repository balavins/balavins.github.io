I have used filelocks aplenty and wanted to keep my main source of refernces here
They maybe the simplest ways to synchronize across multiple processes but could be tricky and painful.

## Filelocks for Synchronization  
Filelocks that I have worked with are  primarily for the purposes of synchronization. 
A simple example is to have an hardware device whose access could be restricted across multiple processes through filelocks
As long as the filelock is not in NFS, using `flock` API works pretty well(Correction: This is fixed in later linux kernel versions).   
## Filelocks for IPC    
There are scenarios where sometimes, you might want to tell an another process some information on top of holding the lock. The superset of flock `fcntl` is used in this cases.


#References on filelocks
[On the brokenness of file locks](pointer.de/blog/projects/locking.html)
[Range Locking](http://www.cs.uleth.ca/~holzmann/C/system/lockfile.html)
[File locking in Linux](https://gavv.github.io/articles/file-locks/)
