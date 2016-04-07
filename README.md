# vdimount
Linux scripts to mount and unmount VDI images as local filesystems

Inspired by Jeff Waugh at Be the Signal http://bethesignal.org/blog/2011/01/05/how-to-mount-virtualbox-vdi-image/

## Installation

1. Clone this git repo
2. Copy vdimount and vdiumount to your path, e.g. `/usr/local/bin`
3. Make sure they are executable: `chmod +x vdimount vdiunmount`


## Mounting
To mount, just run

    vdimount path_to_file.vdi

For example

    vdimount ~/VirtualBoxVMs/Ubuntu/ubuntu.vdi

It will create one block device for the disk itself at /dev/nbd0, and one block device for each partition under nbd0. For example, if your vdi has 3 partitions, then the following devices will be created:

    /dev/nbd0
    /dev/nbd0p1
    /dev/nbd0p2
    /dev/nbd0p3


These in turn will be mounted at `/mntvdi/p<i>`. Continuing our example:

    /mntvdi/p1
    /mntvdi/p2
    /mntvdi/p3

## Unmounting
To unmount, just run

    vdiumount

It will unmount each partition and the block device itself.

## License
See LICENSE file

## Author
Avi Deitcher
https://github.com/deitch
http://www.atomicinc.com

