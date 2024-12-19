# SLSA-1-to-2(Project Whole Enchilada)
## **Overview**
This project is a Jenkins-based CI/CD pipeline designed to transition from SLSA (Supply-chain Levels for Software Artifacts) Level 1 to Level 2 compliance. It includes enhancements for build process security, provenance generation, and source integrity, along with custom plugins for data validation and artifact traceability.
If you would like to see step by step how I went from SLSA 1 to 2 please see git history.

---

## **Features**
- **Source Control Security**:
  - Enforced branch protection and mandatory code reviews.
  - Immutable commit history with authenticated access.
- **Isolated Build Environments**:
  - Builds are executed in isolated environments (e.g., containers) to ensure process separation.
- **Provenance Metadata**:
  - Automatically generate and attach metadata for every build, including commit ID, source repository, and environment details.
- **Custom Plugins**:
  - Data validation plugins to ensure integrity of inputs and build configurations.
- **Dependency Management**:
  - Use of lock files and validation against trusted sources.
- **Build Logs**:
  - Comprehensive logging for auditability and troubleshooting.

---

## **Project Goals**
1. **Transition to SLSA Level 2:**
   - Implement compliance requirements for source integrity, build isolation, and provenance generation.
2. **Custom Solutions:**
   - Develop plugins to handle validation and provenance without relying on pre-built solutions.
3. **Security Enhancements:**
   - Introduce role-based access control and basic secret management.

---

## **Technologies Used**
- **Build System:** Jenkins
- **Version Control:** GitHub/GitLab
- **Build Isolation:** Docker
- **Provenance and Validation Plugins:** Custom plugins developed in Java/Groovy
- **Dependency Management:** NPM/Maven with lock files
- **Artifact Storage:** Artifactory or similar secure repository

---

## **1. File Structure**

```plaintext
├── Jenkinsfile
├── README.md
├── LICENSE
├── .gitignore
├── scripts/
│   ├── validate_data.sh
│   ├── generate_provenance.sh
├── plugins/
│   ├── data-validation-plugin/
│   │   ├── pom.xml
│   │   ├── src/
│   │       ├── main/
│   │       │   ├── java/
│   │       │   │   ├── com/example/datavalidation/
│   │       │   │       ├── Validator.java
│   │       ├── test/
│   │           ├── java/
│   │           │   ├── com/example/datavalidation/
│   │           │       ├── ValidatorTest.java
│   ├── provenance-plugin/
│       ├── pom.xml
│       ├── src/
│           ├── main/
│           │   ├── java/
│           │   │   ├── com/example/provenance/
│           │   │       ├── ProvenanceGenerator.java
│           ├── test/
│               ├── java/
│                   ├── com/example/provenance/
│                       ├── ProvenanceGeneratorTest.java
├── configs/
│   ├── jenkins/
│   │   ├── credentials.xml
│   │   ├── security.groovy
│   ├── docker/
│       ├── Dockerfile
│       ├── docker-compose.yml
├── docs/
│   ├── SLSA_Level_2_Transition.md
│   ├── Provenance_Metadata_Spec.md
├── dependencies/
│   ├── package-lock.json
│   ├── requirements.txt
├── logs/
│   ├── build_logs/
│   │   ├── example_build.log
│   ├── audit_logs/
│       ├── example_audit.log
```

## **Pipeline Workflow**
1. **Source Code Management:**
   - Developers push signed commits to a protected branch.
   - Pull requests with mandatory code reviews ensure source integrity.

2. **Build Execution:**
   - Jenkins triggers isolated builds in Docker containers.
   - Custom plugins validate inputs and configurations.

3. **Artifact Generation and Provenance:**
   - Build artifacts are created and stored securely.
   - Provenance metadata is generated and attached.

4. **Logs and Auditability:**
   - Logs are retained for audit and compliance verification.

---

## **Setup Instructions**
1. **Clone the Repository:**
   ```bash
   git clone https://github.com/<your-repo-name>.git
   cd <your-repo-name>
   ```
2. **Install Dependencies:**
   Ensure you have Docker, Jenkins, and necessary build tools installed.

3. **Configure Jenkins:**
   - Import the pipeline definition (`Jenkinsfile`) into Jenkins.
   - Set up required credentials and secret management.

4. **Run the Pipeline:**
   - Push changes to the repository to trigger the pipeline.

---




## **License**
This project is licensed under the MIT License. 
---

## **Contact**
For questions or support, contact **Ben Simpson** at [devbensimpson@gmail.com].
