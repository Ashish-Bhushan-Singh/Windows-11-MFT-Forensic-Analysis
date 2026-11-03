
# Windows 11 Master File Table (MFT) Forensic Analysis

![Platform](https://img.shields.io/badge/Platform-Windows%2010-blue)
![File System](https://img.shields.io/badge/File%20System-NTFS-green)
![Category](https://img.shields.io/badge/Category-Digital%20Forensics-orange)
![Tools](https://img.shields.io/badge/Tools-Autopsy%20%7C%20MFT%20Explorer-purple)

## Project Overview

This project focuses on examining the Master File Table (MFT) in a Windows 10 NTFS environment.

The MFT is an important component of the NTFS file system. It stores metadata about files and directories.

The investigation uses Autopsy and MFT Explorer to locate, extract, and examine MFT records.

## Objectives

- Understand the NTFS file system.
- Locate the $MFT system file.
- Extract the MFT using Autopsy.
- Load the MFT into MFT Explorer.
- Examine MFT record structures.
- Understand NTFS attributes.
- Analyze file timestamps.
- Understand Data Runs and Bitmap attributes.

## Tools Used

| Tool | Purpose |
|---|---|
| Windows 10 | Investigation environment |
| Autopsy | Digital forensic analysis |
| MFT Explorer | MFT record examination |
| NTFS | File system |

## Investigation Workflow

1. Check the Windows file system.
2. Create an Autopsy case.
3. Add the evidence source.
4. Locate the $MFT file.
5. Extract the MFT.
6. Load the extracted file into MFT Explorer.
7. Examine MFT records.
8. Analyze NTFS attributes.
9. Document findings.

## MFT Record Examination

The first MFT record was examined.

### Observed Record Information

| Field | Observed Value |
|---|---|
| Entry Number | 0 |
| Sequence Number | 1 |
| Offset | 0x0 |
| Flags | InUse |
| File Name | $MFT |
| File Attributes | Hidden, System |
| Parent MFT Record | 5 |

### Examined NTFS Attributes

- $STANDARD_INFORMATION
- $FILE_NAME
- $DATA
- $BITMAP

## Key Findings

- The $MFT file was successfully located.
- The file was extracted using Autopsy.
- MFT Explorer successfully loaded the extracted file.
- MFT record number 0 was examined.
- The record was marked InUse.
- Hidden and System flags were observed.
- Data Runs and Bitmap information were examined.

## Screenshots

Investigation screenshots will be documented in the `screenshots/` directory.

## Learning Outcomes

- Understanding NTFS architecture.
- Understanding MFT record structures.
- Examining file metadata.
- Understanding NTFS attributes.
- Interpreting timestamps.
- Understanding disk cluster allocation.

## Conclusion

This practical provided hands-on experience in Windows NTFS Master File Table analysis.

Autopsy was used to locate and extract the MFT, while MFT Explorer was used to examine its internal records and attributes.

## Disclaimer

This project is for educational and digital forensic learning purposes.

The investigation was conducted on a local Windows 10 system.

No conclusion about malicious activity should be drawn without additional supporting evidence.

---

**Category:** Digital Forensics  
**Operating System:** Windows 10  
**File System:** NTFS  
**Tools:** Autopsy and MFT Explorer
