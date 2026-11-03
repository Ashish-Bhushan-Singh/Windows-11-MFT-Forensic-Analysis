
# Digital Forensics Investigation – MFT Findings Report

## 1. Investigation Details

| Field | Details |
|---|---|
| Project | Windows 10 MFT Forensic Analysis |
| Operating System | Windows 10 |
| File System | NTFS |
| Analysis Tool | MFT Explorer |
| Supporting Tool | Autopsy |
| Examined Artifact | $MFT |
| Examined Record | MFT Entry 0 |

## 2. Investigation Objective

The objective was to examine the Windows NTFS Master File Table and understand the metadata stored within its records.

The investigation focused on identifying MFT record information, NTFS attributes, timestamps, and data allocation details.

## 3. Evidence Examined

The following artifact was examined:

| Artifact | Description |
|---|---|
| $MFT | NTFS Master File Table |
| MFT Entry 0 | Record representing the MFT file itself |

The extracted MFT file was loaded into MFT Explorer.

## 4. Observations

### Observation 1: MFT Record Header

The examined record contained:

- Entry Number: 0
- Sequence Number: 1
- Offset: 0x0
- Flags: InUse
- Reference Count: 0x1

The record was marked as in use.

### Observation 2: File Identification

The filename attribute identified the file as:

`$MFT`

The file was marked with the following flags:

- Hidden
- System

### Observation 3: Timestamp Information

The following timestamps were displayed:

- Created On: 2026-07-30 10:03:54
- Content Modified On: 2026-07-30 10:03:54
- Record Modified On: 2026-07-30 10:03:54
- Last Accessed On: 2026-07-30 10:03:54

All four displayed timestamps were identical.

### Observation 4: Data Attribute

The `$DATA` attribute was identified as Non-Resident.

Observed values:

- Allocated Size: 0x40000
- Actual Size: 0x40000
- Initialized Size: 0x40000

This indicates that the MFT data stream is stored outside the record itself.

### Observation 5: Bitmap Attribute

The `$BITMAP` attribute was identified.

It provides allocation information for MFT record slots.

### Observation 6: Fixup Validation

The parser reported:

`Fixup OK: True`

This indicates successful fixup validation by the parser.

## 5. Technical Findings

| Finding | Result |
|---|---|
| MFT record located | Yes |
| Record marked InUse | Yes |
| Filename identified | $MFT |
| Hidden flag | Present |
| System flag | Present |
| Standard Information | Identified |
| File Name attribute | Identified |
| Data attribute | Identified |
| Bitmap attribute | Identified |
| Data Runs | Identified |
| Fixup validation | Passed |

## 6. Forensic Interpretation

The examined record represents the NTFS Master File Table itself.

The results demonstrate how NTFS stores metadata about system files.

The presence of Hidden and System flags is consistent with the special role of the `$MFT` system file.

The timestamps describe recorded metadata values and do not independently establish a particular user action.

## 7. Limitations

This investigation examined the MFT file's own record.

It did not establish:

- Whether a particular user deleted a file.
- Whether a file was intentionally modified.
- Whether suspicious activity occurred.
- Whether the entire NTFS volume was acquired in a forensically verified manner.

Additional records and supporting evidence would be required for these conclusions.

## 8. Conclusion

The MFT examination was successfully performed using Autopsy and MFT Explorer.

MFT Entry 0 was analyzed, and its header information, filename, standard information, data stream, bitmap, and Data Runs were identified.

This practical provided an introduction to NTFS metadata examination and MFT forensic analysis.

## 9. Final Result

**Status:** MFT record successfully examined.

**Investigation Category:** Digital Forensics.

**Purpose:** Educational NTFS file system analysis.
