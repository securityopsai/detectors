# Windows Process Anomaly Detector

A Python-based security tool that uses machine learning and behavioral analysis to detect suspicious processes on Windows systems. This tool combines static rules, process relationship monitoring, and unsupervised machine learning to identify potentially malicious activity.

## Features

### Machine Learning Detection
- Uses Isolation Forest algorithm to detect anomalous process behavior
- Builds and maintains a baseline of normal process metrics
- Monitors CPU usage, memory consumption, and disk I/O patterns

### Static Analysis
- Detects unsigned executables
- Monitors processes running from suspicious directories (TEMP, APPDATA, Downloads)
- Tracks network connections and flags suspicious combinations

### Process Monitoring
- Real-time monitoring of all system processes
- Tracks process resource usage
- Monitors network connectivity per process
- Built-in whitelist support for common system processes

### Alerting
- Multiple severity levels (INFO, WARNING, ALERT)
- Detailed logging with process information
- Cooldown system to prevent alert spam
- Configurable alert thresholds

## Requirements

- Python 3.8+
- Windows Operating System
- Required Python packages:
  ```
  psutil
  scikit-learn
  numpy
  pefile
  ```

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/securityopsai/detectors.git
   cd detectors
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

Run the detector:
```bash
python ProcessAnomalyDetector
```

The tool will:
1. Load or create a baseline of normal process behavior
2. Start monitoring processes in real-time
3. Generate alerts for suspicious activity
4. Log findings to `enhanced_process_monitor_log.txt`

## Configuration

### Whitelist
Edit the WHITELIST variable to add trusted processes:
```python
WHITELIST = ['explorer.exe', 'svchost.exe', 'chrome.exe']
```

### Suspicious Directories
Modify SUSPICIOUS_DIRECTORIES to adjust monitored locations:
```python
SUSPICIOUS_DIRECTORIES = ['TEMP', 'APPDATA', 'Downloads']
```

### Alert Cooldown
Adjust the COOLDOWN value (in seconds) to control alert frequency:
```python
COOLDOWN = 60  # Seconds between repeated alerts for the same process
```

## Alert Severity Levels

- **INFO**: Minor concerns (e.g., signed executable in suspicious directory)
- **WARNING**: Moderate concerns (e.g., unsigned executable or suspicious parent-child relationship)
- **ALERT**: Major concerns (multiple suspicious indicators or severe anomalies)

## Logging

The tool logs all findings to `enhanced_process_monitor_log.txt` with the following format:
```
YYYY-MM-DD HH:MM:SS [SEVERITY] - Message
```

Example:
```
2024-12-30 10:15:23 [ALERT] - Unsigned, shady directory, and network: suspicious.exe (PID 1234), Path: C:\Users\...\AppData\Local\Temp\suspicious.exe
```

## How It Works

1. **Baseline Creation**
   - Collects metrics from running processes
   - Builds a statistical model of normal behavior
   - Continuously updates baseline data

2. **Anomaly Detection**
   - Uses Isolation Forest to identify outliers
   - Combines ML results with static rules
   - Applies severity-based alerting

3. **Process Analysis**
   - Monitors process creation and termination
   - Tracks resource usage patterns
   - Checks executable signatures
   - Monitors network connections

## Contributing

Contributions are welcome! Areas for improvement:
- Process injection detection
- Memory analysis capabilities
- Additional ML features
- Configuration file support
- Advanced logging options

## Security Notes

- Requires administrative privileges to monitor system processes
- Keep baseline data secure to prevent manipulation
- Regularly update whitelist for your environment
- Monitor the tool's resource usage on critical systems

## License

MIT License - Feel free to use and modify for your needs