Process Detector: Unsupervised Anomaly Detection for Windows Processes - ML Experiment not actual production grade tool

Overview

The Process Detector is a Python-based tool that uses static rules and unsupervised machine learning to detect suspicious processes on Windows systems. By analyzing parent-child relationships, process resource usage, file paths, and network activity, the tool identifies potential threats in real-time.

Features

Unsupervised Learning:

Dynamically learns normal process behavior and flags anomalies using Isolation Forest.

Parent-Child Monitoring:

Tracks unusual relationships (e.g., winword.exe → cmd.exe).

Unsigned Executable Detection:

Flags processes running unsigned executables.

Suspicious Directory Check:

Identifies processes running from directories like TEMP, APPDATA, or Downloads.

Network Monitoring:

Detects processes with active outbound connections.

Integrated Logging:

Logs flagged processes with severity levels (INFO, WARNING, ALERT).

How It Works

Baseline Creation:

Builds a model of normal behavior by analyzing process resource usage and relationships.

Real-Time Monitoring:

Continuously scans processes for anomalies using machine learning and static rules.

Logging:

Records flagged processes with actionable details in a log file.

Installation

Requirements

Python 3.8+

Required Libraries:

psutil

scikit-learn

pefile

pandas

Setup

Clone the repository:

git clone https://github.com/yourusername/process-detector.git
cd process-detector

Install dependencies:

pip install -r requirements.txt

Run the tool:

python process_detector.py

Usage

Run the Detector

Execute the script:

python process_detector.py

The detector will:

Build a baseline of normal process behavior.

Monitor processes in real-time.

Log anomalies to enhanced_process_monitor_log.txt.

Stop Monitoring

Use Ctrl+C to stop the program.

View Logs

Check the log file for flagged processes:


Detection Criteria

Severity

Description

INFO

Signed executables running from suspicious directories.

WARNING

Unsigned executables or abnormal parent-child relationships.

ALERT

Processes with multiple anomalies (e.g., unsigned + shady directory + network activity).

Customization

Whitelist

Add known safe processes to avoid false positives:

WHITELIST = ['explorer.exe', 'svchost.exe', 'chrome.exe']

Suspicious Directories

Modify the list of directories to monitor:

SUSPICIOUS_DIRECTORIES = ['TEMP', 'APPDATA', 'Downloads']

Logging Cooldown

Adjust how often the same process can be logged:

COOLDOWN = 60  # Seconds

How It Learns

The tool collects metrics like CPU usage, memory, disk I/O, and parent-child relationships for all processes.

It trains an Isolation Forest model to identify outliers in this data.

Any process deviating significantly from the baseline is flagged as anomalous.

Roadmap

Add detection for injected DLLs.

Integrate with Windows Event Logs for process creation monitoring.

Implement process runtime analysis for long-running scripts.

Contributing

Feel free to submit issues or pull requests to enhance the functionality of the Process Detector.

License

This project is licensed under the MIT License.

