# PR0FYLER - 1.01: GeneMapper Electropherogram Export Utility

---

## Description
[cite_start]**PR0FYLER** is a Windows Batch script designed to automate the process of exporting electropherograms from **GeneMapper** projects into individual PDF files using the software's command-line interface[cite: 1, 14].

[cite_start]This utility was developed for the **Forensic Biology and DNA Laboratory (Laboratorio de Biologia e DNA Forense)** of the **Scientific Police of Goiás (Polícia Científica de Goiás - PCI/GO)**, Brazil, to streamline forensic DNA analysis data export.

---

## Features
* [cite_start]**Automated Login**: Securely collects the **GeneMapper** username and password[cite: 2]. [cite_start]The password input is masked during typing using a PowerShell script for enhanced security[cite: 2].
* [cite_start]**Intelligent Executable Search**: The script automatically searches for the `GeneMapper.exe` executable[cite: 4]:
    1.  [cite_start]It first checks the common path `C:\AppliedBiosystems` for a fast result[cite: 4].
    2.  [cite_start]If not found, it performs a deep search across all other logical drives using WMIC, looking for the `\AppliedBiosystems` directory structure[cite: 4, 5].
* [cite_start]**Manual Fallback**: If the executable cannot be located automatically, the user is prompted to manually enter the directory path[cite: 7, 8].
* [cite_start]**Dedicated Output Folder**: A new folder, named after the project (e.g., `C:\Users\<Username>\Desktop\<ProjectName>`), is automatically created on the user's desktop to organize the exported PDF files[cite: 12].
* [cite_start]**Detailed Logging**: All execution output and potential errors from the GeneMapper command-line tool are captured in a `log_execucao.txt` file within the export folder[cite: 14, 15].

---

## Requirements
* **Operating System**: Windows.
* **Software**: An installed copy of **Applied Biosystems GeneMapper** (ID or ID-X).
* [cite_start]**Permissions**: The user must have read/execute permissions for the `GeneMapper.exe` file and write permissions to the desktop (`%USERPROFILE%\Desktop`)[cite: 12].

---

## How to Use

1.  **Run the script**: Double-click the `PR0FYLER.bat` file.
2.  [cite_start]**Enter Credentials**: The script will prompt you to enter your GeneMapper **username** and **password**[cite: 2]. *Note: The password input is masked.*
3.  [cite_start]**Enter Project Name**: Input the exact name of the **GeneMapper** project you wish to export[cite: 3].
4.  **Executable Location**:
    * [cite_start]The script will display "Procurando GeneMapper.exe..." (Searching for GeneMapper.exe) and attempt to locate the file automatically[cite: 4].
    * [cite_start]If it fails, you will be prompted to manually enter the full path to the directory containing `GeneMapper.exe`[cite: 7, 9].
5.  [cite_start]**Execution**: The script will then execute GeneMapper using command-line arguments[cite: 13]. [cite_start]Wait for the process to complete.
6.  [cite_start]**Finalization**: Once the process is finished, a summary will display the location of the exported files and the execution log[cite: 15].
    * *Files are located at:* `C:\Users\<YourUsername>\Desktop\<ProjectName>`
    * [cite_start]Press any key to close the window[cite: 16].

---

## Technical Details: Command-line Invocation
[cite_start]The script executes the GeneMapper command line using the following structure for the export process:

```cmd
GeneMapper.exe -commandline -username "<USERNAME>" -password "<PASSWORD>" -project "<PROJECT>" -exportsampleplot "<EXPORTDIR>" -splitfile "true" -outputfilename "samplefilename"
