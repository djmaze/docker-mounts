Mount devices configured via environment variables into a (privileged) Docker container.

This is meant to be used as a [custom storage container](http://docs.rancher.com/os/configuration/storage/#custom-storage-container) for use with [RancherOS](https://github.com/rancher/os).

It is probably not useful for anything else.

## Usage

    MOUNT=/dev/sda1
    MOUNTPOINT=/mnt/disk
    FSTYPE=btrfs

    docker run --privileged --rm -v /lib/modules:/lib/modules:ro \
      --device $MOUNT -v /:/mnt/host -e MOUNT_1=$MOUNT -e MOUNTPOINT_1=$MOUNTPOINT -e FSTYPE_1=$FSTYPE \
      mazzolino/mounts

You can use `MOUNT_2`, `MOUNT_3` and so on in order to do multiple mounts.
