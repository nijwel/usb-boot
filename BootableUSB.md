
## Insert USB Flash drive
4GB or higher for Windows 7 and above
## Open cmd prompt as admin
Right click start menu, click command prompt (admin)
## Run diskpart
```
diskpart
```
## Run list disk
```
list disk
```

```
Exmaple Output

  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
  Disk 0    Online          238 GB      0 B        *
  Disk 1    Online          476 GB      0 B        *
  
 ```
 
 ## Select flash drive to be made bootable
 
 From the output of list disk, select the number of the USB drive that will be bootable
 
 ```
 select disk 2
 
 Disk 2 is now the selected disk.
 ```
 
 ## Remove all contents of flash drive
 **THIS WILL DELETE ALL DATA ON DRIVE**
 
 ```
 clean
 ```
 ## Create partition
 ```
 create partition primary
 ```
 ## Selecte created partition
 ```
 select partition 1
 ```
 ## Format created partition
 ```
 format fs=ntfs quick
 ```
 ## Set created partition as active
 ```
 active
 ```
 ## Exit diskpart
 This will exit diskpart, but leave cmd open
 ```
 exit
 ```
 ## Navigate to OS to be copied
 If the OS is in ISO format, it needs to be mounted and extracted
 
 Example if OS contents is on root of I drive:
 ```
 I:
 ```
 ## Navigate to boot and install bootsector on formated USB drive
 This example is if USB is the L: drive
 ```
 cd boot
 bootsect.exe /nt60 L:
 ```
 ## Copy entire contents of the OS onto the flash drive
 This example is done with the OS being on the root of I: and the flash drive as the drive L:
 ```
 xcopy I:\*.* L:\ /E /H /F
 ```
 
 
 
