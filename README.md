# ClearSafe

## Overview
The **ClearSafe** tool is designed to help app developers and organizations validate their applications' compliance with Google's **Data Safety** requirements. This tool ensures that sensitive data usage, sharing, and permissions align with Google Play's policies, making it easier to maintain transparency and protect user privacy.

## Features
- **Static Analysis**:
  - Scans application source code and metadata (e.g., `AndroidManifest.xml`) to detect sensitive data usage and permissions.
  - Identifies sensitive APIs such as location access, device identifiers, and contact information.

- **Dynamic Analysis**:
  - Monitors app behavior during runtime to detect API calls and network transmissions involving sensitive data.
  - Flags unencrypted data transmissions and unauthorized data sharing.

- **Compliance Reports**:
  - Generates detailed reports highlighting compliance issues.
  - Provides risk scores and actionable recommendations for resolving violations.

- **Developer-Friendly Integration**:
  - CLI for local analysis.
  - REST API for automated integration with CI/CD pipelines.
  - Interactive web dashboard for report visualization.

## Use Cases
- **Developers**:
  - Validate apps before submission to Google Play.
  - Identify and fix data safety issues during development.
- **Organizations**:
  - Monitor compliance across multiple apps.
  - Ensure adherence to privacy regulations and Google Play policies.

## Tech Stack
### Core Components
- **Static Analysis**:
  - Python (e.g., `xml.etree`, `Javaparser`, `Spoon`, `Dart Analyzer`)
  - Tools: `APKTool`, `SourceKitten`
- **Dynamic Analysis**:
  - Frida, MobSF
  - Android Emulator, Xcode Simulator

### Backend
- **Frameworks**: FastAPI (Python) or Express.js (Node.js)
- **Database**: PostgreSQL (for storing reports and metadata)
- **Queue**: RabbitMQ or Kafka (for job processing)

### Frontend
- **Framework**: React (TypeScript)
- **Styling**: Tailwind CSS
- **Visualization**: Chart.js, D3.js

### Tools
- Docker (containerization)
- GitHub Actions or GitLab CI/CD (pipeline integration)

## Installation
### Prerequisites
- Python 3.8+
- Node.js 16+
- Docker (optional for containerized setup)

### Steps
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Alphaxide/clearsafe.git
   cd clearsafe
   ```
2. **Set Up the Backend**:
   ```bash
   cd backend
   pip install -r requirements.txt
   python main.py
   ```
3. **Set Up the Frontend**:
   ```bash
   cd frontend
   npm install
   npm start
   ```
4. **Run the CLI Tool**:
   ```bash
   python cli.py --file path/to/your.apk --output report.json
   ```

## Usage
### CLI
```bash
validate-app --file myapp.apk --output report.json
```

### API
- Endpoint: `/analyze`
- Example Request:
  ```json
  {
    "file": "myapp.apk"
  }
  ```
- Example Response:
  ```json
  {
    "status": "success",
    "issues_found": [
      {
        "type": "Sensitive Data",
        "description": "ACCESS_FINE_LOCATION permission detected."
      }
    ]
  }
  ```

### Web Dashboard
1. Navigate to `http://localhost:3000`.
2. Upload APKs, view compliance reports, and get recommendations.

## Roadmap
- [ ] Add support for iOS app analysis.
- [ ] Extend dynamic analysis capabilities.
- [ ] Integrate with Google Play Console API for automated checks.
- [ ] Add machine learning models to detect sensitive data patterns.

## Contributing
We welcome contributions! Please:
1. Fork the repository.
2. Create a new branch: `git checkout -b feature-name`.
3. Commit your changes: `git commit -m 'Add feature-name'`.
4. Push to the branch: `git push origin feature-name`.
5. Open a pull request.

## License
This project is licensed under the [MIT License](LICENSE).

## Acknowledgments
Special thanks to open-source projects like **Frida**, **MobSF**, and **SonarQube**, which inspire and power parts of this tool.

