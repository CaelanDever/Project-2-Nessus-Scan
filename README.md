# Project-2-Nessus-Scan• Project (2): Nessus Scan::

🎟 Task:

- Install nessus scan on your CentOS Host

- Create 2 new VMs (name them Testva and Testvb....U CAN MODIFY THE VAGRANT FILE INORDER TO AUTOMATE THIS)

- do an ssh keylamp between your CentOS host and all the other servers in your environment ( vm names should ve Testva and Testvb den add it to MobaXterm *steps was shown* )


Completion Criteria: 

Make sure the UI is accessible his step covers how to configure and run a Nessus vulnerability scan on your two VMs (Testva and Testvb). Here's a more detailed guide on setting up and running the scan.

<img width="452" alt="453" src="https://github.com/user-attachments/assets/3fecd063-2742-4f99-8938-53309ba3e753">


🎯 Prerequisites:
Ensure the following are completed before starting:

Nessus is installed and running on your CentOS host.
The Nessus web interface is accessible via https://<CentOS-IP>:8834.
Both VMs (Testva and Testvb) are created using Vagrant and have SSH access set up between the CentOS host and the VMs.
You have the IP addresses of both Testva and Testvb. You can obtain these either by:
Running vagrant ssh-config to get the private network IP addresses of the VMs.
Or SSHing into each VM and using ifconfig or ip addr to find the IP address.
Step-by-Step Process: Run Nessus Scan
1. Access the Nessus UI:
Open your web browser and go to the following URL to access the Nessus Web UI:

https://<CentOS-IP>:8834
If this is your first time accessing Nessus, you’ll need to accept the security exception for the self-signed SSL certificate.
Login to the Nessus web interface using the credentials you set up during the installation.

# 2. Create a New Vulnerability Scan:
Once you're logged into the Nessus UI, you can begin setting up a new scan.

Click "New Scan" in the Nessus dashboard.

Nessus provides various templates for different types of scans. Choose one that fits your requirements.

# 3. Choose the Scan Template:
For this project, a Basic Network Scan is usually sufficient to scan for vulnerabilities across the network.

In the Templates section, click on the Basic Network Scan template.
The Basic Network Scan detects general vulnerabilities such as missing patches, misconfigurations, open ports, etc.

# 4. Configure the Scan Settings:
Once the scan template is selected, you will be taken to the scan configuration page where you will set up the targets and parameters.

Name the Scan:
Give your scan a name (e.g., "VM Vulnerability Scan").

Targets:
Enter the IP addresses of your two VMs (Testva and Testvb) in the Targets field. You can specify multiple IPs or a range, for example:

192.168.56.101, 192.168.56.102
If you're unsure about the IP addresses, run vagrant ssh-config or SSH into the VMs and use the ip addr or ifconfig command to find the IP addresses of Testva and Testvb.
Other Scan Parameters (Optional):

Schedule: You can schedule the scan to run at a specific time if you don't want to start it immediately.
Scan Policy: If necessary, you can adjust the scan policies, but the default settings are generally fine for a basic scan.
For a quick test, default settings should work well.

5. Advanced Settings (Optional):
You can configure additional settings depending on your network and the depth of the scan you want. Some key settings include:

Port Scanning: Specify whether to scan specific ports or all ports.

Credentialed Scanning: If you want to perform a more in-depth scan, you can provide SSH credentials so Nessus can log in and check for internal vulnerabilities (like software versions or system configurations).
You would add the SSH credentials in the Credentials section for Testva and Testvb to run a more detailed vulnerability analysis.

In this project, we'll assume you’re performing an uncredentialed scan (no need for SSH login).

6. Launch the Scan:
Once you've entered all the necessary information:

Click the "Save" button to save your scan configuration.

After saving, you’ll be taken back to the Scans dashboard.

Click the "Launch" button next to your saved scan configuration to start the scan immediately.

7. Monitor the Scan:
Once the scan starts, you will see the progress in the Nessus UI.

You can monitor the status of the scan in real-time, including how many hosts have been scanned, how many vulnerabilities have been detected, and the severity level of those vulnerabilities (low, medium, high, critical).

Scan Progress: Depending on the network and how deep the scan is, it may take a few minutes to several hours to complete. You can refresh the page to check progress.

🎯 Step 6: Reviewing and Interpreting the Scan Results

1. View Scan Results:
After the scan completes, you can review the results directly in the Nessus UI.

In the Scans dashboard, click on the name of the scan you just ran (e.g., "VM Vulnerability Scan").

The results will show a breakdown of vulnerabilities detected on Testva and Testvb, categorized by severity:

Critical
High
Medium
Low

2. View Detailed Reports:
Click on the IP address of Testva or Testvb to see the detailed list of vulnerabilities for that specific VM.

You’ll get a list of detected vulnerabilities along with their severity score (CVSS score) and detailed information, such as:

Description of the vulnerability.
Exploit availability.
Recommendations for remediation.

3. Exporting Reports (Optional):
If you need to export the results for documentation or further analysis, Nessus allows you to export the scan results.

You can export the scan results in formats like HTML, PDF, CSV, or Nessus (the proprietary file format).

To export, click the Export button in the scan results page and choose the desired format.

🎯 Completion Criteria:
Nessus UI Accessible: Make sure the Nessus web interface is accessible at https://<CentOS-IP>:8834 and you can log in.

Run a Scan: Successfully run a scan on both Testva and Testvb. This scan should complete without errors.

VMs Detected: Nessus should be able to detect Testva and Testvb, and identify any vulnerabilities present on these VMs.

Review Results: Ensure the scan results show vulnerabilities (if any) for both VMs.

Troubleshooting:
If the Nessus scan fails or doesn’t detect the VMs, check the following:

Firewall Settings: Ensure that the firewall on the VMs and CentOS host allows the necessary traffic. Open SSH (port 22) and other relevant ports using:


sudo firewall-cmd --zone=public --add-port=8834/tcp --permanent
sudo firewall-cmd --zone=public --add-port=22/tcp --permanent
sudo firewall-cmd --reload

IP Addresses: Double-check the IP addresses of Testva and Testvb to ensure they are correct and reachable from the CentOS host.

Nessus Status: Verify that Nessus is running properly with:

sudo systemctl status nessusd
By completing all of the above steps, you will have successfully installed Nessus, created VMs with Vagrant, 

And run a vulnerability scan on the 2 vms



