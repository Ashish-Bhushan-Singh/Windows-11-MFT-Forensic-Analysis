
# NTFS Timestamps – Digital Forensics Learning Notes

## 1. Introduction

NTFS stores timestamp information about files and directories.

These timestamps can help digital forensic investigators understand when file-system events were recorded.

NTFS maintains timestamp information in attributes such as:

- $STANDARD_INFORMATION
- $FILE_NAME

## 2. Four Important NTFS Timestamps

### 1. Created Time

This timestamp represents when the file or directory was created, according to the relevant metadata attribute.

### 2. Modified Time

This timestamp represents when the file's content was last modified.

It is commonly referred to as the content modification timestamp.

### 3. MFT Record Changed Time

This timestamp represents when the file's MFT metadata record was last modified.

For example, changes to certain file metadata may update this timestamp.

### 4. Last Accessed Time

This timestamp represents the last recorded access time.

Windows may delay or disable last-access timestamp updates for performance reasons.

Therefore, it should not always be treated as an exact record of when someone opened a file.

## 3. Timestamp Example From My Investigation

The following values were observed in MFT Explorer while examining MFT Entry 0.

| Timestamp | Observed Value |
|---|---|
| Created On | 2026-07-30 10:03:54 |
| Content Modified On | 2026-07-30 10:03:54 |
| Record Modified On | 2026-07-30 10:03:54 |
| Last Accessed On | 2026-07-30 10:03:54 |

All four displayed timestamps were identical.

## 4. Difference Between STANDARD_INFORMATION and FILE_NAME

NTFS can store timestamp information in both attributes.

### $STANDARD_INFORMATION

Contains:
- Creation time
- Content modification time
- MFT record modification time
- Last access time

### $FILE_NAME

Also contains:
- Creation time
- Content modification time
- MFT record modification time
- Last access time

These values can differ.

## 5. Why Can Timestamps Differ?

Timestamp differences can occur for several reasons:

- File renaming
- File movement
- Metadata changes
- File copying
- Changes to file content
- Differences in how NTFS updates metadata

A timestamp difference is not automatically evidence of suspicious activity.

## 6. Important Forensic Considerations

When examining timestamps:

1. Identify which attribute contains the timestamp.
2. Compare STANDARD_INFORMATION and FILE_NAME values.
3. Check the system time and time zone.
4. Consider timestamp resolution and rounding.
5. Consider possible clock inaccuracies.
6. Correlate timestamps with other forensic artifacts.
7. Avoid drawing conclusions from one timestamp alone.

## 7. Practical Investigation Exercise

Using MFT Explorer:

1. Select an ordinary file record.
2. Expand STANDARD_INFORMATION.
3. Record its four timestamps.
4. Expand FILE_NAME.
5. Record its four timestamps.
6. Compare both sets of values.
7. Document any differences.

## 8. Findings

During the examination of MFT Entry 0:

- Four timestamp fields were identified.
- All four displayed timestamps were identical.
- Timestamp information was found in STANDARD_INFORMATION and FILE_NAME.
- The importance of comparing both attributes was identified.

## 9. Conclusion

NTFS timestamps are important metadata artifacts in digital forensic investigations.

By examining timestamp values in both STANDARD_INFORMATION and FILE_NAME, investigators can develop a better understanding of file-system metadata changes.

However, timestamps must be interpreted carefully and correlated with other evidence.

## 10. Disclaimer

This document is intended for educational digital forensic learning.

Timestamp values alone do not prove who performed an action or why it occurred.
