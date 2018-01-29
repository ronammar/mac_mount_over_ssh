# Mount over SSH on Apple OS X

Brief instructions to mount a drive onto your mac over SSH. This will integrate in the *Finder* UI, which is very useful.

First, install [sshfs](https://github.com/osxfuse/sshfs/releases/download/osxfuse-sshfs-2.5.0/sshfs-2.5.0.pkg) 
and [FUSE](https://github.com/osxfuse/osxfuse/releases/download/osxfuse-3.7.1/osxfuse-3.7.1.dmg).

Now, in the terminal, create the mount point as a directory. *Do this only once.*

```bash
# Do this only once
sudo mkdir /Volumes/mymount
```

When it's time to mount to your local directory do the following.

```bash
sudo sshfs -o allow_other [USERNAME]@[HOST]:/my/path/to/stuff /Volumes/mymount
```

To unmount:

```bash
sudo umount /Volumes/mymount
```

In this example, I've mounted using `sudo` and put the mount point in `Volumes`. To enable access to non-root users, we use the 
`allow_other` option. This can be omitted when not `sudo`-ing and using a local directory, for example, on `~/Desktop`.

**NOTE: If you are having issues, trying unmounting and re-mounting until you are successful. This is possibly due to a bug in FUSE.**
