# Setup SonarQube for a Node.js project with Github Action

> This sample app demonstrate how to set up SonarQube with GitHub Actions for a Node.js project


## 🛠 Basic Set up - step by step

- You should have a SonarQube server (self-hosted) OR you can use SonarCloud https://www.sonarsource.com/products/sonarcloud/
- After login create SonarQube Token: In SonarQube UI → My Account → Security → Generate Token
- Add the token in GitHub repo: ➔ GitHub → Settings → Secrets and variables → Actions → New Repository Secret:
  -   Name: SONAR_TOKEN
  -   value: your generated token
- Create a file called sonar-project.properties and keep it in root of project:
  ```bash
    sonar.projectKey=your_project_key
    sonar.host.url=https://your-sonarqube-server.com
    sonar.login=${SONAR_TOKEN}
    sonar.sources=src
    sonar.language=js
  ```
  This tells SonarScanner how to scan your project.
- Add GitHub Action Workflow (.github/workflows/sonarqube.yml): add conetnt provided in the Repo.
- Note:
    - If you use SonarCloud, then SONAR_HOST_URL=https://sonarcloud.io
    - sonar-project.properties must be in the project.

## 🔥 How does it work?
- Code is pushed or PR created
- GitHub Action runs
- SonarQube scanner checks your code
- SonarQube dashboard updated with report

## 📦 Installation

```bash
# Clone the repo
git clone https://github.com/rupachowrasia/nodejs-sonarqube-setup-with-github-action.git

# Move into the project directory
cd nodejs-sonarqube-setup-with-github-action

# Install dependencies
npm install

# Run the app
npm run start
