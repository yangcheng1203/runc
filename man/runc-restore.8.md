% runc-restore "8"

# NAME
   runc restore - restore a container from a previous checkpoint

# SYNOPSIS
   runc restore [command options] `<container-id>`

Where "`<container-id>`" is the name for the instance of the container to be
restored.

# DESCRIPTION
   Restores the saved state of the container instance that was previously saved
using the runc checkpoint command.

# OPTIONS
    --image-path value           path to criu image files for restoring
    --work-path value            path for saving work files and logs
    --tcp-established            allow open tcp connections
    --ext-unix-sk                allow external unix sockets
    --shell-job                  allow shell jobs
    --file-locks                 handle file locks, for safety
    --manage-cgroups-mode value  cgroups mode: 'soft' (default), 'full' and 'strict'
    --bundle value, -b value     path to the root of the bundle directory
    --detach, -d                 detach from the container's process
    --pid-file value             specify the file to write the process id to
    --no-subreaper               disable the use of the subreaper used to reap reparented processes
    --no-pivot                   do not use pivot root to jail process inside rootfs.  This should be used whenever the rootfs is on top of a ramdisk
    --empty-ns value             create a namespace, but don't restore its properties
    --auto-dedup                 enable auto deduplication of memory images
    --lazy-pages                 use userfaultfd to lazily restore memory pages
    --lsm-profile value          Specify an LSM profile to be used during restore in the form of TYPE:NAME.

## OPTION DETAILS

**--lsm-profile**

Specify an LSM profile to be used during restore in the form of TYPE:NAME.

`TYPE` can either be *apparamor* or *selinux* and is followed by *:* and a
valid LSM label.
```
runc restore --lsm-profile "selinux:system_u:system_r:container_t:s0:c82,c137" <container-id>
```
