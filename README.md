# Process Anomaly Detection Learning Project

**This is a LEARNING PROJECT designed to understand process monitoring, Python programming, and basic machine learning concepts. It is NOT intended for actual security monitoring or production use.**

## Learning Objectives

This project helps understand:
- How to interact with Windows processes using Python
- Basic machine learning concepts with scikit-learn
- Working with system metrics and logs
- Python programming best practices
- Basic security monitoring concepts

## Project Components

### Process Monitoring
- Using psutil to access process information
- Reading process metrics (CPU, memory, disk I/O)
- Understanding process relationships

### Basic Machine Learning
- Introduction to anomaly detection
- Using Isolation Forest algorithm
- Feature engineering with process data
- Model training concepts

### Python Programming
- Object-oriented programming
- File I/O operations
- Configuration management
- Logging and error handling

## Requirements

- Python 3.8+
- Windows Operating System
- Python packages:
  ```
  psutil
  scikit-learn
  numpy
  pefile
  pyyaml
  ```

## Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/securityopsai/detectors.git
   cd detectors
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Project Structure

- `ProcessAnomalyDetector` - Main Python script
- `config.yaml` - Configuration settings
- `requirements.txt` - Required Python packages

## Key Learning Points

1. **Process Information**
   - How to access process details
   - Understanding process metrics
   - Process relationship concepts

2. **Machine Learning Basics**
   - What is anomaly detection
   - How Isolation Forest works
   - Feature selection and engineering

3. **Python Skills**
   - Working with classes
   - File operations
   - Error handling
   - Configuration management

## Contributing

This is a learning project - feel free to:
- Experiment with the code
- Add new features
- Improve documentation
- Share your learning

## Educational Purpose

This project is designed for:
- Learning Python programming
- Understanding basic security concepts
- Experimenting with machine learning
- Practicing system monitoring

## License

MIT License - Free to use for learning and experimentation

## Important Note

This is purely an educational project for learning purposes. It should not be used for actual security monitoring or in any production environment. The code is meant to demonstrate concepts and may not follow security best practices.
