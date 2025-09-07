# Analysis-of-the-Disk-Structure-using-Sleuth-Kit
# Lubindher S
# 212222240056
## AIM:
To analyze the disk structure of a given disk image using Sleuth Kit tools in Kali Linux.

## REQUIREMENTS
- **Operating System**: Windows 10/11 or Kali Linux
- **Tools**:  
  - [The Sleuth Kit for Windows](https://sleuthkit.org/)  
  - Optional GUI: [Autopsy Forensic Browser](https://www.autopsy.com/)
- **Test Data**: Disk image file (`disk.dd`, `disk.img`, `.E01`)

## ARCHITECTURE DIAGRAM
```mermaid
flowchart TD
    A[Disk Image / Physical Disk] --> B[mmls - Partition Analysis]
    B --> C[fsstat - File System Metadata]
    C --> D[fls - File Listing]
    D --> E[icat - File Recovery]
    E --> F[Recovered Data / Metadata Report]
```
## DESIGN STEPS:
### Step 1:
- Obtain or create a disk image file (e.g., disk.dd) to analyze.
- Open the terminal in Kali Linux.

### Step 2:
Use Sleuth Kit tools like:
 - mmls → Examine the partition layout.
 - fsstat → View file system details.
 - fls → Get file listing.
 - icat → Recover files using inode numbers.
### Step 3:
Interpret the output to understand:
 - Partition table layout
 - File system metadata (block size, creation time, etc.)
 - Deleted and allocated files
 - Inode-based file recovery

## PROGRAM:
Sleuth Kit Disk Analysis Commands
### Partition Analysis
```bash
mmls disk.dd
```
### File System Metadata
```bash
fsstat -o 2048 disk.dd
```
### File Listing
```bash
fls -o 2048 disk.dd
```
### File Recovery
```bash
icat -o 2048 disk.dd 4 > recovered_file.txt
```
- Recovers the file associated with inode 4.
## SAMPLE WORKFLOW 
```
Let’s create a 10MB blank disk image and simulate file system activity:


cd ~/Downloads
```

# Step 1: Create an empty disk image
```
dd if=/dev/zero of=disk.dd bs=1M count=10
```
# Step 2: Format it with a file system (like FAT32)
```
mkfs.vfat disk.dd
```
## OUTPUT:
#### Disk Structure Analysis Results
<img width="640" height="480" alt="VirtualBox_KALI_07_09_2025_18_18_54" src="https://github.com/user-attachments/assets/8184a476-0852-4ea7-b1bc-84519987030d" />

#### Create Disk
<img width="640" height="480" alt="VirtualBox_KALI_07_09_2025_18_23_14" src="https://github.com/user-attachments/assets/318d43f3-cd05-49f0-afac-026dae86bfbe" />

#### fls

```
fls -f fat -o 0 disk.dd
```
<img width="640" height="480" alt="VirtualBox_KALI_07_09_2025_18_30_12" src="https://github.com/user-attachments/assets/7804bcc0-9ca3-443a-a1d8-32627f38123a" />

<img width="640" height="480" alt="VirtualBox_KALI_07_09_2025_18_35_41" src="https://github.com/user-attachments/assets/8acb93c1-6da3-4c46-a41d-7fa6dc0d159d" />



## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.
