**Step 1: Downloading eNSP**

*   **Your Action:** Click on the provided link: [https://forum.huawei.com/enterprise/intl/en/thread/download-ensp-simulator-installation-software-here/667238396713648128?blogId=667238396713648128](https://forum.huawei.com/enterprise/intl/en/thread/download-ensp-simulator-installation-software-here/667238396713648128?blogId=667238396713648128)
*   **Your Action:** On the Huawei Talent Forum page, locate the download link for the eNSP ZIP folder (ensure it's the English version).
*   **Your Action:** Initiate the download.
*   **My Prompt:** Once the download starts, please let me know so we can move to the next step. Also, confirm you've downloaded the English version.

**Step 2: Preparing Your PC**

*   **My Explanation:** Before installing, we need to make sure your computer is ready for eNSP and VirtualBox.
*   **Your Action (i):** **Enable Virtualization in your BIOS/UEFI:**
    *   This process varies depending on your computer's manufacturer. Typically, you access your BIOS/UEFI settings by pressing a key (like Del, F2, F10, F12, or Esc) during startup.
    *   Look for settings related to "Virtualization," "VT-x," or "AMD-V" and enable them. 
    *   Save the changes and restart your computer.
    *   If you are unsure on how to do this please provide me the manufacturer and model of your motherboard or laptop.
*   **Your Action (ii):** **Remove Windows Hypervisor:**
    *   Open Command Prompt as an administrator.
    *   Type the following command and press Enter: `bcdedit /set hypervisorlaunchtype off`
    *   Restart your computer.
*   **Your Action (iii):** **Uninstall any Previous VirtualBox versions:**
    *   Go to "Apps and Features" in Windows settings.
    *   Locate any entries for "Oracle VM VirtualBox."
    *   Select them and click "Uninstall."
    *   Restart your computer.
*   **My Prompt:** Once you've completed these configuration steps and your computer has restarted, let me know.

**Step 3: Installing Applications**

*   **Your Action:** Extract the downloaded eNSP ZIP folder.
*   **Your Action:** Locate the installer for VirtualBox within the extracted folder, run it and install the application by clicking through with the given default options.
*   **Your Action:** Locate the installer for Wireshark within the extracted folder, run it and install the application by clicking through with the given default options.
*   **Your Action:** Locate the installer for eNSP within the extracted folder, run it and install the application by clicking through with the given default options.
*    **My Prompt:** As you're installing each application, be sure to grant all requested permissions. After you finish installing all three, please let me know so we can proceed to step 4.

**Step 4: Launching and Registering the USG6000V Firewall**

*   **Your Action:** Open the eNSP application.
*   **Your Action:** Locate the USG6000V firewall in the device list (usually on the left).
*   **Your Action:** Drag and drop the USG6000V firewall onto the main workspace (topo sheet).
*   **Your Action:** Click the "Menu" button in the top right corner.
*   **Your Action:** Select "Tools" from the dropdown.
*   **Your Action:** Select "Register devices" from the dropdown.
*   **Your Action:** Select ALL the options in the "Register devices" window that appears.
*   **Your Action:** Click "OK" or "Register".
*   **My Prompt:** Once you've registered the devices, please let me know so we can proceed to the firewall startup.

**Step 5: Starting the Firewall and Accessing the CLI**

*   **Your Action:** Right-click on the USG6000V firewall icon on the topo sheet.
*   **Your Action:** Select "Start" from the context menu.
*   **Your Action:** A prompt will appear asking you to select a file; navigate to the installation folder you have the eNSP files and locate the vfw file associated with the USG6000V firewall (it will likely be in a folder specific to the USG). Select it.
*   **Your Action:** Right-click on the USG6000V firewall again.
*   **Your Action:** Select "CLI" from the context menu.
*   **Your Action:** Wait for the CLI window to load (as described in the guide).
*  **My Prompt:**  After the firewall CLI is running, please let me know.

**Step 6 (Optional): Increasing Resources (If needed)**

*   **Your Action:** Close the eNSP application.
*   **Your Action:** Run VirtualBox as administrator.
*   **Your Action:** Select the virtual machine corresponding to the USG6000V (it should be named something like "USG6000V").
*   **Your Action:** Click the "Settings" button.
*   **Your Action:** Select "System".
*   **Your Action:** In the "Memory" section, use the slider to increase the RAM allocation. Be guided by the green band, and don't allocate more RAM than is safely available.
*   **Your Action:** Click "OK"
*   **Your Action:** Restart the eNSP application.
*   **My Prompt:** If you adjusted the VirtualBox settings please let me know to confirm if the steps have been executed correctly

**Let's Begin!**

Are you ready to start with step 1 by downloading the eNSP .ZIP folder? Let me know when it starts.
