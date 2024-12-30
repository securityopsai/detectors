# Windows Process Anomaly Detector (Testing Version)

**IMPORTANT: This is a testing/experimental tool intended for research and learning purposes only. Do not use in production environments without thorough testing and validation.**

A Python-based security tool that uses machine learning and behavioral analysis to detect suspicious processes on Windows systems. This tool combines static rules, process relationship monitoring, and unsupervised machine learning to identify potentially malicious activity.

## Testing Disclaimer

This tool is:
- **Experimental**: Under active development and testing
- **Not Production Ready**: May generate false positives/negatives
- **For Research**: Intended for security research and learning
- **Resource Intensive**: May impact system performance during testing

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
  pyyaml
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
1. Load configuration from config.yaml
2. Start monitoring processes in real-time
3. Generate alerts for suspicious activity
4. Log findings to rotating log files

## Configuration

All configuration is now in `config.yaml`. You can modify:
- Whitelisted processes
- Suspicious directories
- Alert thresholds
- Command line patterns
- Suspicious network ports

## Alert Severity Levels

- **INFO**: Minor concerns (e.g., signed executable in suspicious directory)
- **WARNING**: Moderate concerns (e.g., unsigned executable or suspicious command line)
- **ALERT**: Major concerns (multiple suspicious indicators or severe anomalies)

## Testing Notes

1. **System Impact**
   - Monitor CPU and memory usage during testing
   - Adjust model_retrain_interval in config if needed
   - Consider system load when testing

2. **False Positives**
   - Expect initial false positives while baseline is built
   - Tune thresholds in config.yaml as needed
   - Use whitelist for known-good processes

3. **Testing Environment**
   - Test in isolated/development environment first
   - Back up any important data before testing
   - Monitor system performance during testing

## Known Limitations

- May generate false positives during initial learning period
- Resource intensive during model training
- Limited to Windows operating systems
- Requires administrative privileges
- Experimental machine learning implementation

## Contributing

Contributions are welcome! Areas for improvement:
- Process injection detection
- Memory analysis capabilities
- Additional ML features
- Testing and validation
- Performance optimization

## Security Notes

- This is a testing tool - use with caution
- Requires administrative privileges
- Keep baseline data secure
- Monitor resource usage
- Verify results independently

## License

MIT License - Feel free to use and modify for your needs

## Disclaimer

This software is provided for educational and research purposes only. The authors are not responsible for any damage or misuse of this tool. Always obtain proper authorization before monitoring systems and respect all applicable laws and regulations.