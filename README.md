# DISM-SFC-CHKDSK-Windows-Repair-Guide
A simple guide to check for, &amp; repair corupted, or missing widows files
-
*Brief Overview*
* To use chkdsk, dism, and sfc together, run them in this order:

  - First, use **DISM /Online /Cleanup-Image /RestoreHealth** to repair the Windows image 
  
  - Second, run **sfc /scannow** to fix system files

  - Third, use **chkdsk [DRIVE LETTER] /f /r** to check and repair the hard drive.

This sequence ensures that the system file source (dism) is repaired before sfc 
attempts to fix system files, and chkdsk addresses potential disk corruption after 
the file system has been checked. 
-
***Step By Step***
-
1. Open Command Prompt, or Powershell with admin privileges by clicking the Start button,
then type cmd, or powershell, and right-click on the "Command Prompt", or "Powershell" search result.

2. Select "Run as administrator" from the context menu.

3. Then confirm the User Account Control prompt by clicking "Yes" to launch the Command Prompt,
  or Powershell with elevated privileges. Once the window opens, take note of your drive letter for later.
   Usually Windows is installed on the *C:* Drive.

4. From your chosen window, first type, or paste (Ctrl+V), into the window:
  **DISM /Online /Cleanup-Image /RestoreHealth**
   Then press *Enter* and wait for the process to complete.
<img width="1096" height="632" alt="image" src="https://github.com/user-attachments/assets/b3b4091f-8aa0-4e36-ae30-adca8732314e" />

    *This process can take some time*. The system will scan the Windows image for corrupted files and then download 
    and replace the corrupted files from Windows Update if any are found.
   If the process fails, run it from *Safe Mode*.

6. From your same chosen window, then type, or paste (Ctrl+V), into the window:
  **sfc /scannow**
   Then press *Enter* and wait for the process to complete.

   *This process can take some time*. The process will check the integrity of your system files and repair any it finds corrupted or missing. 

7. Finally, type the following command and press *Enter* to schedule a scan that will run on the next reboot:
  **chkdsk [DRIVE LETTER] /f /r**
   This is where the drive letter you noted earlier is needed, for example, your command may look like
   **chkdsk C: /f /r**
   if Windows in on your *C:* drive.
   The */f* parameter fixes file system errors, and the */r* parameter finds and repairs bad sectors.
   Since we are checking the system drive in this case, you will be prompted to schedule the check for the next system restart. 
  When prompted, type *Y* and press *Enter*.

8. Restart your computer once the processes are finished, and you've scheduled *chkdsk*, for the changes to take effect.
  *chkdsk* will run after your system has restarted.

## ☕ Support the Project

If you find this project helpful and want to support further development by Fulllion Creative Works, consider leaving a tip!

* [Donate via PayPal](https://www.paypal.com/donate/?hosted_button_id=LCDZX75HR4CLC)
* [Support on Ko-fi](https://ko-fi.com/fulllion)

---
© 2026 Fulllion Creative Works. All rights reserved.

