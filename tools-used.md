
# Tools Used – Windows 11 MFT Forensic Analysis

## 1. Introduction

This document describes the tools used during the Windows 10 Master File Table (MFT) forensic investigation.

The tools help identify, extract, and examine NTFS file system metadata.

## 2. Windows 10

**Purpose:** Investigation environment.

Windows 10 was used as the operating system for this practical.

Key activities:
- Checking the file system.
- Identifying the NTFS volume.
- Locating the MFT system file.
- Examining Windows file system structures.

## 3. Autopsy

**Purpose:** Digital forensic investigation.

Autopsy is an open-source digital forensic platform used to examine disk images and file systems.

Activities performed:
- Creating a forensic case.
- Adding a data source.
- Examining NTFS file system contents.
- Locating the `$MFT` file.
- Extracting the MFT for further examination.

Official Website:

https://www.autopsy.com/

Download:

https://www.autopsy.com/download/

## 4. MFT Explorer

**Purpose:** Master File Table examination.

MFT Explorer is a forensic utility developed by Eric Zimmerman.

It provides a graphical interface for examining MFT records.

Activities performed:
- Loading the extracted `$MFT` file.
- Examining MFT record numbers.
- Viewing file names.
- Examining NTFS attributes.
- Reviewing file timestamps.
- Understanding Data Runs.

Official Tools Website:

https://ericzimmerman.github.io/

## 5. NTFS File System

**Purpose:** File system under investigation.

NTFS stands for New Technology File System.

It uses the Master File Table to maintain metadata about files and directories.

Important NTFS components examined:

- `$MFT`
- `$STANDARD_INFORMATION`
- `$FILE_NAME`
- `$DATA`
- `$BITMAP`

## 6. Tool Comparison

| Tool | Main Function |
|---|---|
| Windows 10 | Investigation environment |
| Autopsy | File system forensic examination |
| MFT Explorer | MFT record analysis |
| NTFS | File system structure |

## 7. Why These Tools Were Selected

Autopsy was selected to locate and extract the MFT from the examined NTFS volume.

MFT Explorer was selected to examine the binary MFT data and display its records in a readable format.

Together, these tools provide a practical learning environment for NTFS forensic analysis.

## 8. Conclusion

The tools used in this investigation helped demonstrate how digital forensic investigators examine Windows file system metadata.

They provided practical experience in locating, extracting, and interpreting Master File Table records.

## Disclaimer

This documentation is intended for educational and authorized forensic examination purposes.
