# Cyber Ninjas - Docker Sandboxing for APK Analysis

Cyber Ninjas is a powerful Android pentesting framework that leverages Docker to create a secure sandbox environment for analyzing APK files. This ensures that all analysis is performed in an isolated environment, protecting the host system from potential risks while providing detailed insights into vulnerabilities, hardcoded secrets, and privacy risks.

---

## Features
- **Secure Environment**: Each APK is analyzed in an isolated Docker container, ensuring no interference with the host system.
- **Reproducibility**: Consistent environments across different systems using Docker images.
- **Automation**: Simplified setup and execution with Docker commands.
- **Detailed Reports**: Generates comprehensive analysis reports in JSON and PDF formats.
- **Web Interface**: User-friendly web interface for uploading APKs and viewing results.

---

## Prerequisites
Before you begin, ensure you have the following installed:
1. **Docker**: [Install Docker](https://docs.docker.com/get-docker/)
2. **Python**: Version 3.11 or higher
3. **Git**: To clone the repository

---

## Setup Instructions

### 1. Clone the Repository
Clone the repository to your local machine:
```bash
git clone <repository-url>
cd Cyber-Ninjas-GGI-Hackthon
```

### 2. Build the Docker Image
Build the Docker image for the project:
```bash
docker build -t apk-analyzer .
```

### 3. Run the Docker Container
Run the container and expose the application on port `5000`:
```bash
docker run -p 5000:5000 apk-analyzer
```

### 4. Access the Web Interface
Visit the web interface in your browser:
```
http://localhost:5000
```

---

## Using the Framework

### 1. Upload APK for Analysis
- Navigate to the **Upload APK** section on the web interface.
- Select your APK file and click **Analyze**.

### 2. Analyze the APK
- The application processes the APK in the Docker container.
- It performs static analysis to detect vulnerabilities, hardcoded secrets, and privacy risks.

### 3. View and Download Reports
- Once the analysis is complete, detailed reports are generated in JSON and PDF formats.
- Download the reports from the **Results** section.

---

## One-Line Setup Command (For Linux)
For quick setup on Linux, use the following one-liner:
```bash
sudo apt update && sudo apt install -y docker.io && sudo systemctl start docker && sudo systemctl enable docker && sudo docker build -t apk-analyzer . && sudo docker run -p 5000:5000 apk-analyzer
```

---

## Cleaning Up

### Stop the Docker Container
To stop the running container:
```bash
docker ps
docker stop <container-id>
```

### Remove the Docker Container
To remove the container:
```bash
docker rm <container-id>
```

---

## Troubleshooting

### Common Issues
1. **Docker Daemon Not Running**:
   Ensure Docker is running on your system:
   ```bash
   sudo systemctl start docker
   ```

2. **Port Already in Use**:
   If port `5000` is already in use, run the container on a different port:
   ```bash
   docker run -p 8080:5000 apk-analyzer
   ```

3. **File Not Found Errors**:
   Verify that the `static` folder contains all required files (e.g., CSS, images).


## Contributing
We welcome contributions! If you’d like to improve this project, feel free to fork the repository and submit a pull request. You can also open an issue to report bugs or suggest new features.

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for more details.

---

## Contact
For any questions or support, feel free to reach out:
- **Email**: support@cyberninjas.com
- **Website**: [Cyber Ninjas](http://localhost:5000)
