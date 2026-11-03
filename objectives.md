
# Investigation Objectives

## Project Name
Windows 10 Master File Table (MFT) Forensic Analysis

## 1. Purpose

The purpose of this investigation is to understand and examine the Master File Table (MFT) used by the Windows NTFS file system.

This practical provides hands-on experience in identifying, extracting, and analyzing MFT records using digital forensic tools.

## 2. Primary Objectives

- Identify the NTFS file system on Windows 10.
- Locate the `$MFT` system file.
- Understand the role of the Master File Table.
- Use Autopsy to locate and extract the MFT.
- Load the extracted MFT into MFT Explorer.
- Examine individual MFT records.
- Understand MFT record numbers and sequence numbers.
- Identify important NTFS attributes.

## 3. Technical Objectives

Understand the following NTFS attributes:

| Attribute | Purpose |
|---|---|
| $STANDARD_INFORMATION | Stores file metadata and timestamps |
| $FILE_NAME | Stores filename and parent directory information |
| $DATA | Represents file data streams |
| $BITMAP | Tracks allocated MFT record slots |
| $ATTRIBUTE_LIST | References additional attributes |

## 4. Timestamp Investigation

Examine the following timestamps:

- Created time
- Content modified time
- Record modified time
- Last accessed time

Understand why timestamps may differ.

## 5. Expected Learning Outcomes

After completing this practical, I aim to understand:

1. NTFS file system architecture.
2. MFT record structure.
3. File metadata storage.
4. NTFS file attributes.
5. File timestamp interpretation.
6. Data Runs and cluster allocation.
7. Basic digital forensic investigation procedures.

## 6. Investigation Scope

This investigation focuses on the Windows 10 NTFS file system and the examination of MFT records.

The findings are limited to the examined evidence and available forensic artifacts.

## 7. Tools

- Windows 10
- Autopsy
- MFT Explorer

## 8. Conclusion

These objectives provide a structured approach to learning NTFS Master File Table analysis and developing practical digital forensic investigation skills.
