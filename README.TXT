COPYSYS.G4B v0.5 (2024116), by deomsh

Function: copy MS-DOS' IO.SYS, MSDOS.SYS, COMMAND.COM and optional DRVSPACE.BIN/ DBLSPACE.BIN (or ONE other file) from ONE specified directory to target and set attributes (not on other file)

Use 1: COPYSYS.G4B [DEVICE1]PATH1 DEVICE2 [DRVSPACE.BIN|DBLSPACE.BIN|somefile]

Use 2: COPYSYS.G4B [/?] (this text)

Remarks: 

Does not shift directory-entries in root, disk MUST be empty up to MS-DOS 6.22. Empty disk with volume-label (MS-DOS <=6.22): label is shifted up two entries

Grubutil FAT needed in: %~dp0, (bd), (bd)/GRUB, (bd)/G4DLL, or ROOT

If source device is not given, from root-device ('/' is still needed)

Short File Names in PATH1 only

Third switch: full file name only! Instead of DRVSPACE.BIN or DBLSPACE.BIN or one other file can be copied (but other file's attributes will NOT be set to 'RSH'!)

Asks to overwrite existing MSDOS.SYS on target, other files ALWAYS overwritten

FAT-source: Modification Date and Modification Time set on copied target-files

Example 1: COPYSYS.G4B (hd0,0) (fd1)

Example 2: COPYSYS.G4B (hd0,0)/MSDOS622/ (rd)

Example 3: COPYSYS.G4B (fd1)/system/ (hd1,0) DRVSPACE.BIN

Example 4: COPYSYS.G4B (fd0) (hd1,0) DBLSPACE.BIN

Example 5: COPYSYS.G4B (fd0) (rd) SYS.COM
  
ATTRIB-related sub-routines: see their descriptions in ATTRIB.G4B (but simplified: target-path in COPYSYS.G4B is always '/')

Returns: message and variable 'result=1' if successfull, otherwise error-messages and 'result=0'

BTW PBR-bootcode NOT written, but grub4dos wil boot IO.SYS without if 'chainloader /io.sys' is used (on MSDOS <=6.22 only with 'chainloader (disknumber)+1')

History
v0.5
1) if LABEL is present on MSDOS<=6.22 shift to THIRD entry and write E5 to first TWO entries for IO.SYS/MSDOS.SYS (if needed)
2) if MSDOS <=6.22 start only if root of target device is fully empty and not FAT32
3) MSDOS <=6.22 'detected' if MSDOS.SYS >=4KB
4) Grub4Dos: >=20170505 checked
5) attributes copied from fat32 or from source-directory other than '/'
6) more protection - some command-lines not accepted
7) 'COPYSYS /?' for help too
8) ask to overwrite existing MSDOS.SYS
9) insmods/ delmod fat
10) give back original debug status
11) copy modification date/-time

v0.4.2:  
Protected against other number of File Allocation Tables than one or two (number of FAT's: 1 or 2)  

v0.4.1: first published version
