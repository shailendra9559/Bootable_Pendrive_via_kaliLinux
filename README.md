# Bootable_Pendrive_via_kaliLinux
it make bootable pendrive using .sh script and it doess not require to install any other package to install it just use dd and other system commands to do so
# Bootable Pendrive Creation Script

This Bash script allows you to create a bootable USB pendrive from a specified .iso file.

## Usage

1. Run the script:
   ```bash
   ./bootablePendrive.sh
    Follow the prompts to:
        Select the pendrive from the list of attached drives.
        Enter the path to the .iso file.
2.  Confirm the formatting and creation of the bootable pendrive.

3. Wait for the process to complete.

Notes

    Ensure the pendrive is not mounted before running the script.
    The script uses mkfs.ntfs to format the pendrive. Adjust this command based on your preference.
    The script uses the dd command to create the bootable pendrive.

Disclaimer

Use this script at your own risk. Be cautious when selecting the pendrive, as it will be formatted, and data will be lost.
