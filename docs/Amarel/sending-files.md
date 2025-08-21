---
title: Transferring Files to Amarel
nav_order: 4
nav_enabled: true 
parent: Amarel Computing
---


### Sending Files to and from Amarel
Let’s assume you’re logged-in to a local workstation or laptop and not connected to Amarel. To send files from your local system to your Amarel /home directory,

```bash
scp file-1.txt file-2.txt <NetID>@amarel.rutgers.edu:/home/<NetID>
```

To pull a file from your Amarel /home directory to your laptop (note the “.” at the end of this command),

```bash
scp <NetID>@amarel.rutgers.edu:/home/<NetID>/file-1.txt .
```

If you want to copy an entire directory and its contents using scp, you’ll need to “package” your directory into a single, compressed file before moving it:

```bash
tar -czf my-directory.tar.gz my-directory
```

After moving it, you can unpack that .tar.gz file to get your original directory and contents:

```bash
tar -xzf my-directory.tar.gz
```

A handy way to synchronize a local file or entire directory between your local workstation and the Amarel cluster is to use the rsync utility. First, let's sync a local (recently updated) directory with the same directory stored on Amarel:

```bash
rsync -trlvpz work-dir gc563@amarel.rutgers.edu:/home/gc563/work-dir
```

In this example, the rsync options I'm using are:

- t (preserve modification times)
- r (recursive, sync all subdirectories)
- l (preserve symbolic links)
- v (verbose, show all details)
- p (preserve permissions)
- z (compress transferred data)

To sync a local directory with updated data from Amarel:

```bash
rsync -trlvpz <your NetID>@amarel.rutgers.edu:/home/<your NetID>/work-dir work-dir
```

Here, we've simply reversed the order of the local and remote locations.

For added security, you can use SSH for the data transfer by adding the e option followed by the protocol name (SSH, in this case):

```bash
rsync -trlvpze ssh <your NetID>@amarel.rutgers.edu:/home/<your NetID>/work-dir work-dir
```



### Transferring Files to and from Amarel
- [Basics of moving files to/from the cluster](https://sites.google.com/view/cluster-user-guide#h.3jyxmx35y8y2)
- [Transferring files with external institute using cloud bucket](https://sites.google.com/view/cluster-user-guide#h.dbytkcny0aip)
- [With GCP](https://sites.google.com/view/cluster-user-guide#h.d4yd0653roo5)
- [With AWS](https://sites.google.com/view/cluster-user-guide#h.omfmnbxkx74k)
- [Transferring files using Globus Personal Connect](https://sites.google.com/view/cluster-user-guide#h.sndo8v81d03c)
- [Transferring files to cloud storage using rclone](https://sites.google.com/view/cluster-user-guide#h.zgtvv015l57n)
- [Setting-up your rclone configuration on Amarel](https://sites.google.com/view/cluster-user-guide#h.x36410dl5ede)
- [Using rclone to move files](https://sites.google.com/view/cluster-user-guide#h.7q3loifijbjs)
- [Splitting large files](https://sites.google.com/view/cluster-user-guide#h.og2qx4q6913s)
- [Passwordless access and file transfers using SSH keys](https://sites.google.com/view/cluster-user-guide#h.jgwrkm9e9rwg)
