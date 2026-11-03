
# MFT Record Analysis Using MFT Explorer

## 1. Introduction

This document explains the examination of the Windows 10 Master File Table (MFT) using MFT Explorer.

The extracted `$MFT` file was loaded into MFT Explorer to inspect its internal records and NTFS attributes.

The first MFT record, Entry 0, was selected for analysis.

## 2. Objective

- Examine the internal structure of an MFT record.
- Understand the record header.
- Identify NTFS attributes.
- Interpret file metadata.
- Understand Data Runs.
- Examine MFT record allocation information.

## 3. Tool Used

**MFT Explorer**

MFT Explorer is a graphical forensic utility developed by Eric Zimmerman.

Official tools website:

https://ericzimmerman.github.io/

## 4. MFT Record Header

The following values were observed:

| Field | Observed Value |
|---|---|
| Entry-seq # | 0x0-0x1 |
| Offset | 0x0 |
| Flags | InUse |
| Log Sequence # | 0x205151 |
| Reference Count | 0x1 |
| MFT Base Record | 0x0-0x0 |

### Analysis

- Entry number 0 represents the MFT file itself.
- Sequence number 1 identifies the current record generation.
- Offset 0x0 indicates the beginning of the MFT stream.
- InUse indicates that the record is marked as allocated.
- Reference Count indicates the number of directory references reported by the parser.

## 5. $STANDARD_INFORMATION Attribute

The following information was observed:

| Field | Observed Value |
|---|---|
| Attribute Type | StandardInformation |
| Attribute Number | 0x0 |
| Size | 0x60 |
| Content Size | 0x48 |
| Resident | True |
| Flags | Hidden, System |
| Security ID | 0x100 |

### Timestamps

| Timestamp | Observed Value |
|---|---|
| Created On | 2026-07-30 10:03:54.4268718 |
| Content Modified On | 2026-07-30 10:03:54.4268718 |
| Record Modified On | 2026-07-30 10:03:54.4268718 |
| Last Accessed On | 2026-07-30 10:03:54.4268718 |

### Analysis

The `$STANDARD_INFORMATION` attribute contains metadata and timestamps associated with the file.

The Hidden and System flags indicate that the file is marked as hidden and as a system file.

All four displayed timestamps are identical in this record.

These timestamps should not independently be treated as proof of a specific user action.

## 6. $FILE_NAME Attribute

The following information was observed:

| Field | Observed Value |
|---|---|
| Attribute Type | FileName |
| Attribute Number | 0x3 |
| File Name | $MFT |
| Flags | Hidden, System |
| Name Type | DosWindows |
| Physical Size | 0x4000 |
| Logical Size | 0x4000 |
| Parent MFT Record | 0x5-0x5 |
| Resident | True |

### Analysis

The `$FILE_NAME` attribute contains the filename and parent directory reference.

The parent MFT record number 5 identifies the root directory.

The reported filename namespace is DosWindows.

## 7. $DATA Attribute

The following information was observed:

| Field | Observed Value |
|---|---|
| Attribute Type | Data |
| Attribute Number | 0x6 |
| Resident | False |
| Starting VCN | 0x0 |
| Ending VCN | 0x3F |
| Allocated Size | 0x40000 |
| Actual Size | 0x40000 |
| Initialized Size | 0x40000 |

### Analysis

The `$DATA` attribute describes the file's data stream.

Non-Resident indicates that the data is stored outside the MFT record itself.

The MFT data is represented using cluster mappings called Data Runs.

## 8. Data Runs Analysis

Observed Data Run:

| Field | Value |
|---|---|
| Cluster Offset | 0x119AA |
| Number of Clusters | 0x40 |

### Hexadecimal Conversion

- 0x119AA = 72,106
- 0x40 = 64
- 0x40000 = 262,144 bytes

The Data Run describes a mapping of the non-resident data stream to disk clusters.

The interpretation of the cluster offset requires the volume's cluster size and run-list context.

## 9. $BITMAP Attribute

The following information was observed:

| Field | Observed Value |
|---|---|
| Attribute Type | Bitmap |
| Attribute Number | 0x5 |
| Resident | False |
| Starting VCN | 0x0 |
| Ending VCN | 0x1 |
| Allocated Size | 0x2000 |
| Actual Size | 0x1008 |
| Initialized Size | 0x1008 |

### Analysis

The Bitmap attribute associated with the MFT tracks which MFT record slots are allocated.

It helps NTFS manage available MFT records.

A bitmap value of 1 represents an allocated slot, while 0 represents an unallocated slot.

## 10. Fixup Information

Observed information:

- Expected: 02-00
- Actual: 00-00 | 00-00
- Fixup OK: True

### Analysis

NTFS uses update sequence arrays to detect incomplete or inconsistent multi-sector record updates.

The parser reported Fixup OK: True.

This indicates that its fixup validation passed.

## 11. Key Findings

The examination identified:

1. MFT Entry 0.
2. Record status marked InUse.
3. Filename `$MFT`.
4. Hidden and System flags.
5. Four timestamp fields.
6. Non-Resident Data attribute.
7. Data Run information.
8. Bitmap allocation information.
9. Successful fixup validation.

## 12. Conclusion

The first MFT record was successfully examined using MFT Explorer.

The analysis provided practical knowledge of the MFT record header, standard information, filename metadata, data stream mapping, and bitmap allocation.

This exercise demonstrates how NTFS maintains and organizes file system metadata.

## 13. Forensic Limitations

This analysis concerns the MFT file's own record, not an ordinary user document.

The displayed timestamps and metadata should be interpreted in context.

Additional evidence is required before making conclusions about user activity or file manipulation.
