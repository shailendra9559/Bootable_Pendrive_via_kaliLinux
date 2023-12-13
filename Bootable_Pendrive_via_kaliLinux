#!/bin/bash

echo "List of attached pendrives:"
lsblk -o NAME,SIZE,TYPE,MOUNTPOINT | grep "disk"

read -rp "Enter the pendrive device name (e.g., sda): " pendrive

if [[ ! -e "/dev/$pendrive" || ! $(lsblk -o NAME | grep -w "$pendrive") ]]; then
    echo "Invalid pendrive device. Exiting."
    exit 1
fi

read -rp "Enter the path to the .iso file: " iso_path

if [[ ! -e "$iso_path" || ! "$iso_path" =~ \.iso$ ]]; then
    echo "Invalid .iso file path. Exiting."
    exit 1
fi

echo "Selected Pendrive: /dev/$pendrive"
echo "Selected ISO: $iso_path"

read -rp "Are you sure you want to format /dev/$pendrive? (y/n): " confirm

if [[ "${confirm,,}" != "y" ]]; then
    echo "Operation canceled. Exiting."
    exit 1
fi

# Unmount partitions if they are mounted
sudo umount "/dev/${pendrive}"*

echo "Formatting /dev/$pendrive..."
sudo mkfs.ntfs -f "/dev/$pendrive"

echo "Creating bootable pendrive from $iso_path..."
sudo dd if="$iso_path" of="/dev/$pendrive" bs=4M status=progress

echo "Syncing file system..."
sync

echo "Ejecting /dev/$pendrive..."
sudo eject "/dev/$pendrive"

echo "Bootable pendrive creation complete!"
