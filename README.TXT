COPYSYS.G4B v0.4.1 (20220728), by deomsh

Function: copy MS-DOS' IO.SYS, MSDOS.SYS, COMMAND.COM and optional DRVSPACE.BIN/ DBLSPACE.BIN from ONE specified directory to target and set attributes

Use: COPYSYS.G4B <[DEVICE1]PATH1> <DEVICE2> [DRVSPACE.BIN|DBLSPACE.BIN]

Remarks: Grubutil FAT needed

If source device is not given, from root-device

Short File Names in PATH1 only

Switch: file-name only!

Does not overwrite existing MSDOS.SYS

Example 1: COPYSYS.G4B (hd0,0) (fd1)
  
Example 2: COPYSYS.G4B (fd1)/system/ (hd1,0) DRVSPACE.BIN
  
Example 3: COPYSYS.G4B (fd0) (hd0,0) DBLSPACE.BIN
  
ATTRIB-related sub-routines: see their descriptions in ATTRIB.G4B (but simplified: target-path in COPYSYS.G4B is always '/')

Returns: messages and variable 'result=1' if successfull, otherwise messages and 'result=0'

BTW PBR-bootcode NOT written, but grub4dos wil boot IO.SYS without if 'chainloader /io.sys' is used

History
v0.4.1: first published version
