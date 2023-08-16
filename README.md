# Bell System Monitoring for macOS

The Bell macOS Monitoring script is a Python-based monitoring tool designed to collect and report various system metrics from macOS-based servers. It provides functionalities for monitoring system performance, tracking resource usage, checking for updates, and sending alerts. The script is intended to be run as a background service and can be customized to suit specific monitoring needs.

**Overview**
The script utilizes various Python libraries and system commands to gather information about the system's performance, resource utilization, network activity, and more. It communicates with a remote server to report the collected data, allowing users to monitor their macOS server's health and status remotely.

**Features**
System Information: The script collects and reports essential system information, including the global IP address, hostname, uptime, and operating system version.

**Update Check** 
The script periodically checks for updates and downloads and installs them if available, ensuring that the monitoring tool is up-to-date.

**Resource Monitoring** 
The script monitors CPU usage, memory usage, disk usage, network bandwidth, and other system resources.

**Temperature Monitoring**: 
The script gathers temperature data from system sensors, providing insights into the server's thermal state.

**Process Monitoring**: 
It tracks running processes and their CPU usage, allowing users to monitor the performance of individual processes.

**Alerting Mechanism**s: 
The script can be configured to send alerts based on predefined thresholds for disk usage, swap usage, and network latency.

**Service Status Monitoring**: 
It checks the status of a specific service and can trigger server reboot or shutdown actions based on the server's status.

**Usage**
**Dependencies**: 
The script relies on various Python libraries, including psutil, requests, and others. Make sure these dependencies are installed.

**Configuration**: 
Configure the script by modifying the settings at the beginning of the script. Customize alert thresholds, URLs, and other parameters to match your requirements.

**Execution**: 
Run the script as a background service. It will continuously gather data and send it to a remote server for monitoring.

**Alerts**
Configure alerting mechanisms by setting threshold values for resource usage. The script will send alerts if resource usage exceeds the specified thresholds.

**Note**
The script has been tailored to integrate with the bellbots.eu platform, where the provided IP address is used for verification purposes. This script includes features for handling errors and reporting them to a remote server. The structure of the script is organized into various functions, each serving distinct roles in the monitoring and reporting process.

**Disclaimer**
This script is provided as a starting point for creating a monitoring tool and may require additional adjustments to work seamlessly with your system and network environment. It's important to review and test the script in a controlled environment before deploying it to production systems.

**Important Note**
This script is intended to be used exclusively with a booked service on the bellbots.eu platform. The provided IP address is crucial for verification, and unauthorized use is strictly prohibited. Ensure that you have a legitimate booking on bellbots.eu and have entered the correct IP address for verification. Unauthorized use may result in account suspension or legal action.

**Installation and Usage Guide**
**Prerequisites**

macOS-based server
Python 3.x installed
Internet connectivity

**Installation Steps**
**Clone the Repository**
Open a terminal and navigate to the directory where you want to store the monitoring script. Clone the repository using the following command:

  git clone gh repo clone bellnetwork/bellsys_moni_macos

  cd bellsys_moni_macos
  
**Install Dependencies**

  brew install mpstat
  
  brew install coreutils
  
  brew install bpytop

Install Python3:

  brew install python3 python3-pip

Install the required Python dependencies using pip:

  pip3 install psutil requests

**Run the Script**

Run the script in the background as a service. You can do this using a terminal command:

  python3 sys_check.py &
  
This command starts the script in the background. You can exit the terminal, and the script will continue running.

**Usage Guide**
**Monitoring Data**:
The script will continuously monitor various metrics, such as CPU usage, memory usage, network activity, and more.

**Alerts** 
If configured, the script will send alerts when predefined thresholds are exceeded.

**Update Check**
The script will periodically check for updates and install them if available. This ensures the monitoring tool is up-to-date.

**Remote Monitoring** 
The collected data is sent to a remote server for monitoring. Configure the URLs in the script to match your remote server's endpoints.

**Stopping the Script**

To stop the script, you need to find its process ID (PID) and use the kill command. Follow these steps:

Use the following command to list all background processes:

  ps aux | grep sys_check.py
  
Identify the process ID (PID) of the script.

Use the kill command to stop the script by sending the appropriate signal. Replace <pid> with the actual process ID.

  kill <pid>
  

**Setup launchctl**

Edit and move the .plist file. Please ensure that you entered the correct path.

  vi com.bellsyscheck.plist

  mv com.bellsyscheck.plist /Library/LaunchDaemons/com.bellsyscheck.plist

Run the following commands to load and start the service:
  sudo launchctl load /Library/LaunchDaemons/com.bellsyscheck.plist
  
  sudo launchctl start com.bellsyscheck

**Verify the Service:**

You can check the status of the service using the launchctl command:
sudo launchctl list | grep com.bellsyscheck

You should see output indicating that the service is loaded and running.

**Logs:**

The standard output and standard error logs are written to the paths specified in the <string> elements of the .plist file (/var/log/bellsyscheck.log and /var/log/bellsyscheck_error.log, respectively).

**Unload and Stop the Service:**

To stop and unload the service, you can use the following commands:

  sudo launchctl stop com.bellsyscheck

  sudo launchctl unload /Library/LaunchDaemons/com.bellsyscheck.plist

Please note that modifying system-level settings like launchd requires administrative privileges and can impact system behavior. Always use caution and test thoroughly in a controlled environment before deploying to production systems.

**Customization and Advanced Usage**

Please note that the script's core functionality is tightly integrated with the bellbots.eu platform, and unauthorized modifications may cause the script to malfunction or behave unpredictably. We strongly discourage any modifications to the script's existing codebase.

If you have ideas for new features or improvements, we encourage you to share your suggestions with us. You can create a new support ticket on bellbots.eu to propose new features or discuss potential enhancements. Our team will review your suggestions and consider them for future updates to the script.

While you are not allowed to directly modify the script's core code, you can still enhance its capabilities by suggesting new monitoring functions, alert mechanisms, or additional system metrics. Your feedback is valuable to us and can contribute to the ongoing improvement of the Bell macOS Monitoring script.

As for customizing the script's behavior, you can adjust the intervals at which data is collected, alerts are checked, and updates are performed. However, please exercise caution and ensure that any changes align with the intended functionality and usage of the script within the context of the bellbots.eu service.

Thank you for your understanding and cooperation in adhering to the script's usage guidelines. If you have any questions or suggestions, please don't hesitate to reach out to us through the support channels provided on bellbots.eu.
