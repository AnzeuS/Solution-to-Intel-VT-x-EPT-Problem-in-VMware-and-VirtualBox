# Solution to Intel VT-x/EPT Problem in VMware and VirtualBox

[Versión en español](https://github.com/AnzeuS/Solucion-problema-intel-VT-x-EPT-VMware---VirtualBox)


This guide describes the solution to an issue related to Intel VT-x/EPT virtualization. It was tested on Windows 11 Pro with an Intel i5 12th generation processor.

- VMware Workstation
<img src="https://github.com/user-attachments/assets/ba3b7b48-b1bb-4af9-bb0c-085330b6de2e" alt="Intel VT-x/EPT VMware Issue intel vtx vmware issue" width="500" />

- Oracle VirtualBox
<img src="https://github.com/user-attachments/assets/981ecee1-af95-4696-a9bc-50f19d41efc9" alt="Intel VT-x/EPT VirtualBox Issue intel vtx virtualbox issue" width="500" />

---

## Introduction
To solve this issue, we assume that Intel virtualization is already enabled in the BIOS. If the problem persists, follow the steps below.

---

## Steps to resolve the issue

1. **Verify the message in `systeminfo`**
   - Open a `cmd` window and run `systeminfo`.
   - If the message appears:
     
     ```
     Hypervisor has been detected. Features required for Hyper-V will not be displayed.
     ```
     
     <img src="https://github.com/user-attachments/assets/2cdf744e-e9fa-4db4-9777-d78f2668ffb7" alt="Systeminfo Verification" />

     proceed with the following steps.

2. **Disable Core Isolation**
   - Go to Settings > Device Security > Core Isolation.
   - Turn off this option.

   <img src="https://github.com/user-attachments/assets/fe8ac965-7ac9-4b51-bb6b-b8ad8bdc189c" alt="Core Isolation" width="500" />

3. **Modify `gpedit.msc` settings**
   - Press `Windows + R`, type `gpedit.msc`, and navigate to the following option:

     ```
     Computer Configuration > Administrative Templates > System > Device Guard > Virtualization Based Security
     ```
   - Disable it.

   <img src="https://github.com/user-attachments/assets/b5a8acc5-23af-4f2c-825d-140d1889d33d" alt="Gpedit Configuration" width="500" />

4. **Disable Windows features**
   - Go to "Add or Remove Windows Features".
     
   <img src="https://github.com/user-attachments/assets/43a0f566-0c9b-46b8-894c-0030be1ea434" alt="Windows Features" width="500" />
   
   - Turn off the following options:
     - Hyper-V
     - Windows Hypervisor Platform
     - Virtual Machine Platform

   <img src="https://github.com/user-attachments/assets/0b0478b0-75ce-4a9f-8684-73b26e597bba" alt="Windows Features" width="500" />

5. **Restart and verify**
   - Restart your computer.
   - Open `cmd`, run `systeminfo`, and confirm the following information appears:

     ```
     A hypervisor has not been detected. Features required for Hyper-V will not be displayed.
     ```
## Issue Solved:

- VMware
<img src="https://github.com/user-attachments/assets/578514d7-62a4-4d09-866c-5161c74b3378" alt="Intel VT-x/EPT VMware issue solved" width="500" />

- Oracle VirtualBox
<img src="https://github.com/user-attachments/assets/a71cfb6c-ec15-4f80-9e19-877bf60875c4" alt="Oracle VirtualBox issue Solved" width="500" />

   <img src="https://github.com/user-attachments/assets/0dfb356f-c5ff-4f96-88ac-0a8f6f92768f" alt="Systeminfo Verification" width="500" />

---
