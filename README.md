# Ultimate Windows Credential Dumper

A comprehensive BadUSB payload for the FlipperZero that performs a full system reconnaissance and credential dump on any Windows machine. This payload is designed for stealth and efficiency, extracting sensitive data and exfiltrating it to a user-defined Discord webhook.

## ⚠️ Disclaimer

This tool is intended for educational purposes and authorized security testing only. Do not use this tool on any device or network for which you do not have explicit, written permission. Misuse of this software can result in severe legal consequences. The authors are not responsible for any misuse or damage caused by this payload.

## 🎯 Features

- **Full System Reconnaissance:** Gathers detailed system information, including OS, hardware specs, running security software, and network configuration.
- **Wi-Fi Profile Extraction:** Retrieves all saved Wi-Fi network names and passwords in clear text.
- **Windows Credential Manager Dumper:** Dumps all saved credentials stored in the Windows Credential Manager, including RDP, website, and application passwords.
- **Windows Vault Dumper:** Extracts credentials from the Windows Vault, including web credentials and other sensitive tokens.
- **File Hunter:** Searches the user's profile directories for high-value files like KeePass databases, private keys, and cryptocurrency wallets.
- **Stealthy Exfiltration:** Uses `curl.exe` to upload a single, clean report file to your Discord webhook, bypassing many character limits and detection methods.
- **Self-Destructing:** Automatically deletes the created report file and terminates the PowerShell process after execution to minimize forensic evidence.

## 📋 How to Use

1.  **Get a Discord Webhook:**
    *   In your Discord server, go to `Channel Settings > Integrations > Webhooks`.
    *   Create a new webhook and copy its URL.

2.  **Configure the Payload:**
    *   Open the `payloads/Ultimate-Credential-Dumper.txt` file.
    *   Replace `YOUR_WEBHOOK_URL_HERE` with your actual Discord Webhook URL.
    *   Save the file.

3.  **Load to FlipperZero:**
    *   Copy the contents of the `.txt` file.
    *   Open the FlipperZero's `BadUSB` app and paste the payload.

4.  **Deploy:**
    *   Plug the FlipperZero into the target Windows machine.
    *   Wait for the payload to execute. The PowerShell window will open and close automatically.
    *   Check your Discord channel for the `FinalReport.txt` file.

## 📁 What's in the Report?

The generated report contains the following sections:

-   **System Information:** Hostname, User, OS, RAM, CPU, Motherboard.
-   **Security Posture:** List of running security software (AV, EDR), Windows Defender status, and firewall rules.
-   **Network Reconnaissance:** IP addresses and active TCP connections.
-   **File Hunt:** Paths to any found sensitive files (`.kdbx`, `.key`, etc.).
-   **Wi-Fi Profiles:** All saved Wi-Fi networks and their passwords.
-   **Windows Credentials:** A full dump of the Credential Manager (`cmdkey /list`).
-   **Windows Vault:** Contents of the Web Credentials and Windows Credentials vaults.

## 🔧 Customization

You can easily modify the payload to suit your needs:

-   **Change File Search:** Edit the `$searchPatterns` array in the payload to look for different file extensions.
-   **Adjust Reconnaissance:** Add or remove PowerShell commands in the script to gather more or less information.
-   **Change Exfiltration Method:** While `curl.exe` is reliable, you can replace the upload line with another method if desired.

## 🤝 Contributing

Contributions are welcome! Feel free to submit a Pull Request with improvements, new features, or bug fixes. Please ensure your code follows the existing style and is well-documented.

## 📜 License

This project is licensed under the **MechEnterprise License**.

## ⭐ Support

If you find this useful, please consider giving the repository a star!
