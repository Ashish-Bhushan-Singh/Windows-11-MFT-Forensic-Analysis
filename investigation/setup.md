
# Investigation Setup – Windows 10 MFT Analysis

## 1. Overview

This document describes the preparation of the Windows 11 environment for Master File Table (MFT) forensic examination.

The investigation focuses on an NTFS-formatted Windows volume.

## 2. Investigation Environment

| Component | Details |
|---|---|
| Operating System | Windows 10 |
| File System | NTFS |
| Forensic Tool | Autopsy |
| MFT Analysis Tool | MFT Explorer |
| Target Volume | Local C: drive |

## 3. Verify the NTFS File System

The first step was to verify the file system of the Windows C: drive.

### Procedure

1. Open File Explorer.
2. Select This PC.
3. Right-click Local Disk (C:).
4. Select Properties.
5. Locate the File System field.
6. Verify that the file system is NTFS.

### Observation

The Windows C: drive was identified as an NTFS volume.

## 4. Launch Autopsy

Autopsy was opened to begin the forensic examination.

### Procedure

1. Launch Autopsy.
2. Select New Case.
3. Enter the case name:

   `Windows10_MFT_Analysis`

4. Choose a case storage directory.
5. Complete the case creation process.

## 5. Add the Data Source

The local disk option was selected during the Autopsy data source configuration.

### Procedure

1. Open the created case.
2. Select Add Data Source.
3. Choose Local Disk if supported by the installed version.
4. Identify the target NTFS volume.
5. Follow the available configuration steps.

### Important Forensic Note

The examination was performed against a live Windows system.

A live-system examination may modify system state and does not guarantee a consistent forensic image.

For evidence preservation, a verified forensic disk image and documented acquisition process are recommended.

## 6. Configure Ingest Modules

Autopsy provides ingest modules to process and examine evidence.

Relevant modules include:

- File Type Identification
- Recent Activity
- Hash Lookup

Module availability depends on the installed Autopsy version and configuration.

The ingest process was allowed to complete before examining the file system.

## 7. Locate the MFT

The Master File Table is stored in a protected NTFS system file named:

`$MFT`

Its NTFS path is:

`C:\$MFT`

The file was located during the examination of the NTFS volume.

## 8. Extract the MFT

The `$MFT` file was extracted from the examined data source for further analysis.

The extracted copy was used for examination in MFT Explorer.

## 9. Preparation Summary

The following activities were completed:

- Windows 10 environment identified.
- NTFS file system verified.
- Autopsy case created.
- Local disk selected for examination.
- Ingest processing performed.
- `$MFT` located.
- MFT extracted for further examination.

## 10. Conclusion

The Windows 11 environment was prepared for MFT analysis using Autopsy.

The extracted MFT file was subsequently examined using MFT Explorer.

This preparation provided the foundation for investigating NTFS file records and metadata.

## 11. Disclaimer

This practical was conducted for educational purposes on a local Windows environment.

The live-system examination should not be considered equivalent to a controlled forensic acquisition.
