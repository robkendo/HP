# HP
Tshoot commands

Hpssacli Commands
When you type the command hpacucli/hpssacli, it will display a “=>” prompt as shown below where you can enter all the hpacucli commands:

root@ximunix:~# hpssacli
HP Smart Storage Administrator CLI 2.10.14.0
Detecting Controllers...Done.
Type "help" for a list of supported commands.
Type "exit" to close the console.
 
=> ctrl all show

Smart Array P400 in Slot 1                (sn: XXXXXXXXXXXXXX)

=> quit
 
 
root@ximunix:~# hpssacli ctrl all show

Smart Array P400 in Slot 1                (sn: XXXXXXXXXXXXXX)
Controller Commands
## Display detail of Controller
hpssacli ctrl all show config

## Display detail of Controller
hpssacli ctrl all show config detail

## Display status of Controller
hpssacli ctrl all show status

## Rescan for New Devices
hpssacli rescan
 
 

Physical Drive Commands
## Display detail information of all physical drives
hpssacli ctrl slot=0 pd all show

## Display detail information of single physical drive
hpssacli ctrl slot=0 pd 2:3 show detail

## Display status of all physical drives
hpssacli ctrl slot=0 pd all show status

## Display status of single physical drive
hpssacli ctrl slot=0 pd 2:3 show status

## To Erase the physical drive (WARN!)
hpssacli ctrl slot=0 pd 2:3 modify erase

## To enable the LED of a physical drive
hpssacli ctrl slot=0 pd 2:3 modify led=on

## To disable the LED of a physical drive
hpssacli ctrl slot=0 pd 2:3 modify led=off
 
 
 
 
 
 
 
 
 
 
 



Logical Drive Commands
## Display detail information of all logical drives
hpssacli ctrl slot=0 ld all show

## Display detail information of single logical drive
hpssacli ctrl slot=0 ld 4 show

## Display status of all logical drives
hpssacli ctrl slot=0 ld all show status

## Display status of single logical drive
hpssacli ctrl slot=0 ld 4 show status

## Re-enabling failed drive
hpssacli ctrl slot=0 ld 4 modify reenable forced

## Create logical drive with RAID 0 using one drive
hpssacli ctrl slot=0 create type=ld drives=1:12 raid=0

## Create LogicalDrive with RAID 1 using two drives
hpssacli ctrl slot=0 create type=ld drives=1:13,1:14 size=300 raid=1

## Create LogicalDrive with RAID 5 using five drives
hpssacli ctrl slot=0 create type=ld drives=1:13,1:14,1:15,1:16,1:17 raid=5

## Delete a specific logical drive
hpssacli> ctrl slot=0 ld 4 delete

## Expanding a logical drive by adding two more drives
hpssacli> ctrl slot=0 ld 4 add drives=2I:1:6,2I:1:7

## Extending the logical drive
hpssacli> ctrl slot=0 ld 4 modify size=500 forced

## Add two spare disks
hpssacli> ctrl slot=0 array all add spares=2I:1:6,2I:1:7
 
## Disable Cache
hpssacli ctrl slot=0 modify dwc=disable

## Modify Accelerator Ratio (read/write):
hpssacli ctrl slot=0 modify cacheratio=25/75

## Enable Array Acceleration for one of your logical drives use:
hpssacli ctrl slot=0 ld 4 modify aa=enable

## Enable Array Acceleration for all of your logical drives use:
hpssacli ctrl slot=0 ld all modify arrayaccelerator=enable


Generate Diagnostic ADU Report
hpssacli ctrl all diag file=/tmp/ADUreport.zip ris=on xml=on zip=on




Command to show if the storage battery has failed
$ hpssacli ctrl all show status
Smart Array P440ar in Slot 0 (Embedded)
Controller Status: OK
Cache Status: Permanently Disabled
Battery/Capacitor Status: Recharging

 
 

