
# NTFS MFT Attributes – Digital Forensics Learning Notes

## 1. Introduction

The Master File Table (MFT) is an essential component of the NTFS file system.

Each MFT record contains attributes that store information about files and directories.

During forensic investigations, these attributes help investigators understand file metadata, timestamps, file names, and data storage.

This document explains the important NTFS attributes examined using MFT Explorer.

## 2. What Are MFT Attributes?

MFT attributes are individual structures inside an MFT record.

Each attribute stores a particular type of information about a file or directory.

Attributes can be:

- Resident
- Non-Resident

## 3. $STANDARD_INFORMATION

### Purpose

The `$STANDARD_INFORMATION` attribute stores basic file metadata.

### Information Stored

- Creation timestamp
- Content modification timestamp
- MFT record modification timestamp
- Last access timestamp
- File flags
- Security information

### Example From Investigation

The `$MFT` record contained:

```text
Flags: Hidden|System

Created On: 2026-07-30 10:03:54
Content Modified On: 2026-07-30 10:03:54
Record Modified On: 2026-07-30 10:03:54
Last Accessed On: 2026-07-30 10:03:54
```

### Forensic Importance

These timestamps can help investigators understand recorded file-system metadata.

However, timestamps must be interpreted with care and should not independently be treated as proof of user activity.

## 4. $FILE_NAME

### Purpose

The `$FILE_NAME` attribute stores information about a file's name and parent directory.

### Information Stored

- Filename
- Parent directory MFT reference
- File size information
- File timestamps
- Filename namespace

### Example From Investigation

```text
File name: $MFT
Flags: Hidden|System
Physical Size: 0x4000
Logical Size: 0x4000
Parent MFT Record: 0x5-0x5
```

### Forensic Importance

The `$FILE_NAME` attribute helps investigators identify file names and directory relationships.

A file can have multiple filename attributes, for example when it has different filename namespaces.

## 5. $DATA

### Purpose

The `$DATA` attribute represents a file's data stream.

### Types

**Resident Data**

The data is stored directly inside the MFT record.

**Non-Resident Data**

The data is stored outside the MFT record in disk clusters.

### Example From Investigation

```text
Resident: False

Allocated Size: 0x40000
Actual Size: 0x40000
Initialized Size: 0x40000
```

### Forensic Importance

The `$DATA` attribute helps investigators understand how file contents are represented and stored.

## 6. $BITMAP

### Purpose

The `$BITMAP` attribute associated with the MFT tracks allocated and unallocated MFT record slots.

### Example From Investigation

```text
Resident: False

Allocated Size: 0x2000
Actual Size: 0x1008
Initialized Size: 0x1008
```

### Forensic Importance

The bitmap helps NTFS manage available MFT record slots.

A set bit indicates an allocated record slot, while an unset bit indicates an unallocated slot.

## 7. $ATTRIBUTE_LIST

### Purpose

The `$ATTRIBUTE_LIST` attribute identifies additional attributes associated with a file record.

It can reference attributes stored in extension MFT records.

### Forensic Importance

It helps investigators understand files whose attributes cannot all fit inside a single MFT record.

## 8. Resident vs Non-Resident Attributes

| Feature | Resident | Non-Resident |
|---|---|---|
| Storage | Inside MFT record | Outside MFT record |
| Data Runs | Not required | Used to map data |
| Common Usage | Small data | Larger data streams |
| Disk Clusters | Not separately allocated for attribute content | Used for data storage |

## 9. Important Forensic Considerations

- Multiple filename attributes may exist.
- Timestamp values may differ between attributes.
- Deleted records may retain metadata.
- Non-resident data uses cluster mappings.
- MFT records can reference extension records.
- Attribute information must be interpreted in context.

## 10. Conclusion

NTFS attributes provide important information about files and directories.

By examining `$STANDARD_INFORMATION`, `$FILE_NAME`, `$DATA`, and `$BITMAP`, investigators can better understand the internal structure of the NTFS file system.

MFT Explorer makes these structures easier to examine during forensic investigations.
