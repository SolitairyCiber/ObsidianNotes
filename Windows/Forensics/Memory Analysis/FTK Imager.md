Use FTK Imager to track down and piece together **McGreedy**'s deleted digital breadcrumbs, exposing his evil scheme. Learn how to perform the following with FTK Imager:

- Analyse digital artefacts and evidence.
- Recover deleted digital artefacts and evidence.
- Verify the integrity of a drive/image used as evidence.

Join **McSkidy**, **Forensic McBlue**, and the team in this digital forensic journey! Expose the corporate conspiracy by navigating through cyber clues and unravelling **McGreedy**'s dastardly digital deeds.

AntarctiCrafts Parking Lot & The Unsuspecting Frostling

**Van Sprinkles**, wrestling with his conscience, scatters USB drives loaded with malware. Little do the AntarctiCrafts employees know, a storm's brewing in their network.

**Van Jolly**, shivering and clueless, finds a USB drive in the parking lot. Little does she know that plugging it in will unleash a digital disaster crafted by the vengeful **McGreedy**. But this is exactly what she does.

Upon reaching her desk, she immediately plugs in the USB drive.

An Anonymous Tip and Confrontation With Van Jolly

Amidst the digital chaos of notifications and alerts from the cyber attack, **McSkidy** gets a cryptic email. It's **Van Sprinkles**, ridden with guilt, nudging her towards exposing **McGreedy** without blowing his own cover.

**McSkidy**, with a USB in hand, reveals to **Van Jolly** the true nature of her innocent find – a tool for digital destruction! Shock and disbelief play across **Van Jolly**'s face as **McSkidy** explains the gravity of the situation and the digital pandemonium unleashed upon their network by the insidious device.

**McSkidy**, **Forensic McBlue** and the team, having confiscated the USB drive from **Van Jolly**, dive into a digital forensic adventure to unravel a web of deception hidden in the device. Every line of code has a story. **McSkidy** and the team piece it together, inching closer to the shadow in their network.

Investigating the Malicious USB Flash Drive

In our scenario, the write-protected USB drive that **McSkidy** confiscated will automatically be attached to the VM upon startup. The VM mounts an emulated USB flash drive, **"\\PHYSICALDRIVE2 - Microsoft Virtual Disk [1GB SCSI]"** in read-only mode to replicate the scenario where a physical drive, connected to a write blocker, is attached to an actual machine for forensic analysis.

  

When applied in the real world, a forensics lab analyst will first note the suspect drive/forensic artefact details, such as the vendor/manufacturer and hardware ID, and then mount it with a write-blocking device to prevent accidental data tampering during forensic analysis.

FTK Imager

|   |   |
|---|---|
|![FTK Imager Logo](https://tryhackme-images.s3.amazonaws.com/user-uploads/63da722f2d207d0049da10b1/room-content/cb64e7b1e02c87966c903d9f40ee2a08.png)|FTK Imager is a forensics tool that allows forensic specialists to acquire computer data and perform analysis without affecting the original evidence, preserving its authenticity, integrity, and validity for presentation during a trial in a court of law.|

Working With FTK Imager

Open **FTK Imager** and navigate to `File > Add Evidence Item`, select `Physical Drive` in the pop-up window, then choose our emulated USB drive **"\\PHYSICALDRIVE2 - Microsoft Virtual Disk [1GB SCSI]"** to proceed.

![Adding an evidence item using FTK Imager](https://tryhackme-images.s3.amazonaws.com/user-uploads/63da722f2d207d0049da10b1/room-content/88ed441cbcafc54ad8b5c8dec6aed905.png)

  

![Selecting a physical drive as an evidence source](https://tryhackme-images.s3.amazonaws.com/user-uploads/63da722f2d207d0049da10b1/room-content/cec6c1bc55012367443dce64401ab63e.png)

  

FTK Imager: User Interface (UI)

|   |
|---|
|FTK Imager's interface is intuitive and user-friendly. It displays an "x" icon next to deleted files and includes key UI components vital for its functionality. These components are:<br><br>1. **Evidence Tree pane**: Displays a hierarchical view of the added evidence sources such as hard drives, flash drives, and forensic image files.<br>2. **File List pane:** Displays a list of files and folders contained in the selected directory from the evidence tree pane.<br>3. **Viewer pane:** Displays the content of selected files in either the evidence tree pane or the file list pane.|

![FTK Imager User Interface (UI)](https://tryhackme-images.s3.amazonaws.com/user-uploads/63da722f2d207d0049da10b1/room-content/9d6cf661865c811b7bcda308496e2602.png)

  

FTK Imager: Previewing Modes

|   |
|---|
|FTK Imager presents three distinct modes for displaying file content, arranged sequentially from left to right, each represented by icons enclosed in yellow:<br><br>1. **Automatic mode:** Selects the optimal preview method based on the file type. It utilises Internet Explorer (IE) for web-related files, displays text files in ASCII/Unicode, and opens unrecognised file types in their native applications or as hexadecimal code.<br>2. **Text mode:** Allows file contents to be previewed as ASCII or Unicode text. This mode is useful for revealing hidden text and binary data in non-text files.<br>3. **Hex mode:** Displays files in hexadecimal format, providing a detailed view of file data at the binary (or byte) level.|

![FTK Imager Previewing Mode - Automatic/IE](https://tryhackme-images.s3.amazonaws.com/user-uploads/63da722f2d207d0049da10b1/room-content/95d24cdc6d382c1b89f5af989c1be9b7.png)

  

Use `Ctrl + F` to search for specific text within a file while in either text or hex preview mode.

![FTK Imager Previewing Mode - Find Xiaomi in Hex mode](https://tryhackme-images.s3.amazonaws.com/user-uploads/63da722f2d207d0049da10b1/room-content/8ad39dd0de241fae81acedf698579775.png)

  

FTK Imager: Recovering Deleted Files and Folders

To view and recover deleted files, expand directories in the File List pane and Evidence Tree pane. Right-click and select `Export Files` on individual files marked with an "x" icon or on entire directories/devices for bulk recovery of files (whether deleted or not).

![FTK Imager - Recovering deleted file](https://tryhackme-images.s3.amazonaws.com/user-uploads/63da722f2d207d0049da10b1/room-content/4e915c80d85efa7c992d76021fc6f6bd.png)

  

![FTK Imager - Recovered deleted file](https://tryhackme-images.s3.amazonaws.com/user-uploads/63da722f2d207d0049da10b1/room-content/1fd732351d04f0636e19f0b0bce64001.png)

  

FTK Imager: Verifying Drive/Image Integrity

To verify the integrity of a drive/image, click on it from the **Evidence Tree** pane and navigate to `File > Verify Drive/Image` to obtain its MD5 and SHA1 hashes.

![FTK Imager - Verify Drive/Image](https://tryhackme-images.s3.amazonaws.com/user-uploads/63da722f2d207d0049da10b1/room-content/2e379d61330d4c6d9c09ebd30dc601d8.png)

  

![FTK Imager - Verify Drive/Image in Progress](https://tryhackme-images.s3.amazonaws.com/user-uploads/63da722f2d207d0049da10b1/room-content/cd2b401779b4bde0d861e12449d46967.png)

  

Practical Exercise With FTK Imager

Use what you have learned today to analyze the contents of the USB drive and answer the questions below.

**IMPORTANT:** Please use **Hex** mode instead of **Text** mode to avoid crashing FTK Imager when processing files as text.