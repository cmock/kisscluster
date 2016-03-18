#!/bin/sh
# this nukes a VM from the cluster
name=$1
drbdadm disconnect $name
drbdadm down $name
drbdadm wipe-md $name
rm /etc/drbd.d/$name.res
systemctl disable vm-$name.service
rm /etc/systemd/system/vm-$name.service
systemctl daemon-reload
lvremove /dev/vmvg/${name}_*
