
# Master File Table (MFT) Extraction Using Autopsy

## 1. Introduction

The Master File Table (MFT) is a core component of the Windows NTFS file system.

It contains records describing files and directories stored on an NTFS volume.

The MFT is stored in a protected system file named `$MFT`.

This practical documents how the MFT was located and extracted using Autopsy.

## 2. Objective

The objectives of this practical are:

- Locate the `$MFT` system file.
- Understand its location in NTFS.
- Extract the MFT using Autopsy.
- Save a copy for further forensic examination.
- Prepare the extracted file for MFT Explorer.

## 3. Tool Used

**Autopsy**

Autopsy is an open-source digital forensic platform used to examine disk images and file systems.

Official website:

https://www.autopsy.com/

## 4. MFT File Location

The MFT is stored in the NTFS system file:

`$MFT`

The commonly referenced path on the Windows C: volume is:

`C:\$MFT`

The file is protected by Windows and is not normally visible as an ordinary file in File Explorer.

## 5. Extraction Procedure

### Step 1: Open Autopsy

Launch Autopsy and open the previously created investigation case.

Case Name:

`Windows10_MFT_Analysis`

### Step 2: Locate the NTFS Volume

Expand the data source and browse the NTFS file system.

### Step 3: Locate the MFT File

Find the `$MFT` system file in the examined NTFS volume.

### Step 4: Select the MFT File

Select the `$MFT` entry in Autopsy.

### Step 5: Extract the File

Use the available file extraction option to save a copy of the selected file.

### Step 6: Save the Extracted File

Save the extracted copy in a dedicated working directory.

Example:

`C:\MFT_Practice\`

The extracted copy is used for further analysis.

## 6. Verification

After extraction, verify that:

- The extracted file exists.
- The filename is `$MFT`.
- The file size is recorded.
- The extracted file is not modified before analysis.

For stronger forensic verification, calculate and record a cryptographic hash such as SHA-256.

## 7. Next Stage

The extracted `$MFT` file is loaded into MFT Explorer.

MFT Explorer is used to parse the binary data and display individual MFT records.

## 8. Important Forensic Considerations

- Preserve the original evidence.
- Work with a forensic copy.
- Document the acquisition method.
- Record file hashes.
- Keep investigation notes.
- Do not publish private disk contents.

## 9. Conclusion

The `$MFT` system file was located and extracted using Autopsy.

The extracted file was prepared for examination with MFT Explorer.

This exercise demonstrates the initial stage of Windows NTFS MFT forensic analysis.

## 10. Disclaimer

This documentation describes an educational forensic exercise.

A live-system extraction is not equivalent to a verified bit-for-bit forensic acquisition.
