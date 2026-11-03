
# NTFS File System – Learning Notes

## 1. What is NTFS?

NTFS stands for New Technology File System.

It is a file system developed by Microsoft and used by Windows operating systems.

NTFS provides features such as:

- File and directory management
- File permissions
- Metadata storage
- File compression
- Encryption support
- Journaling
- Large file support

## 2. What is the Master File Table?

The Master File Table (MFT) is a core component of NTFS.

It contains records describing files and directories on an NTFS volume.

Each file and directory has an associated MFT record.

## 3. Important NTFS System Files

| System File | Purpose |
|---|---|
| $MFT | Stores file and directory records |
| $MFTMirr | Maintains a copy of critical initial MFT records |
| $LogFile | Maintains NTFS transaction log information |
| $Bitmap | Tracks allocated and free clusters |
| $Boot | Contains NTFS boot sector information |
| $Secure | Stores NTFS security information |
| $UpCase | Contains uppercase character mapping information |
| $Extend | Contains extended NTFS metadata files |

## 4. MFT Record Structure

An MFT record contains:

- Record header
- Attribute information
- File metadata
- File name information
- Data stream information

## 5. Resident and Non-Resident Attributes

### Resident Attribute

Data is stored directly inside the MFT record.

### Non-Resident Attribute

Data is stored outside the MFT record in disk clusters.

## 6. NTFS File Allocation

NTFS uses clusters to organize disk storage.

A cluster is a group of disk sectors.

Non-resident attributes use Data Runs to describe the locations of their data.

## 7. Why NTFS Matters in Digital Forensics

NTFS metadata can help investigators examine:

- File creation and modification times
- File names and directory relationships
- File allocation information
- Deleted file records
- File system activity

## 8. Conclusion

Understanding NTFS is essential for examining Windows file system artifacts.

The Master File Table provides important metadata that can support digital forensic investigations.
