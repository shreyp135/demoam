# Multi-Platform Matrix Build Demo

This repository demonstrates a matrix build using GitHub Actions.

Challenge ID: 55db92a  
Contact: 23f3001694@ds.study.iitm.ac.in
HAAaaaaaaaaaa


## EXT4 Filesystem commands
### Create EXT4 filesystem
`sudo mkfs.ext4 /dev/sdb1
`
### Mount EXT4 partition
`sudo mkdir /mnt/ext4test
sudo mount /dev/sdb1 /mnt/ext4test
`
### Check EXT4 details
`sudo dumpe2fs -h /dev/sdb1
`
### Journaling Mode Configuration
`sudo tune2fs -o journal_data_ordered /dev/sdb1` <br>
`sudo tune2fs -o journal_data_writeback /dev/sdb1`<br>
`sudo tune2fs -o journal_data_journal /dev/sdb1
`

## NTFS Filesystem Testing Commands
### Run chkdsk (check & repair)
`chkdsk C: /f /r`

### Query NTFS USN Change Journal
`fsutil usn queryjournal C:`

### View NTFS ACLs
`icacls C:\TestFolder`

### Encrypt folder using EFS
`cipher /e C:\SecureData`


## Crash Simulation

### Force Linux kernel panic
`echo c | sudo tee /proc/sysrq-trigger
`
## Post-Crash Recovery
### EXT4 fsck
`
sudo fsck.ext4 -v /dev/sdb1
`
### NTFS chkdsk
`
chkdsk C: /f
`


## Integrity Verification
### Generate baseline checksums
`find /mnt/ext4test -type f -exec sha256sum {} \; > baseline.sha256`

### Verify checksums after crash
`sha256sum -c baseline.sha256`

## Performance Measurement
### Measure copy speed
`time rsync -a /source/data/ /mnt/ext4test/`

### Drop caches before testing
`sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"`

### Disk I/O monitoring
`iostat -x 1 10`


