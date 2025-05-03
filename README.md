# Setup SonarCloud for a Node.js project with Github Action

> This sample app demonstrate how to set up SonarCloud with GitHub Actions for a Node.js project.
> We use SonarQube to automated code quality + security checker. It saves you from bad code, bugs, and vulnerabilities.

## 📢 SonarQube vs SonarCloud
- SonarQube: Self-hosted (you install it), Full control, Free Community Edition available
- SonarCloud: Cloud-hosted (SaaS), Easy setup, Free for open source projects

## 🛠 Basic Setup - step by step

- You should have a SonarQube server (self-hosted) OR you can use SonarCloud https://www.sonarsource.com/products/sonarcloud/ [Here in this repo we will be using SonarCloud]
- Sign in with GitHub
- After login create SonarQube Token: → My Account → Security → Generate Token
- Import your organization / repository
- Create a new project — choose automatic GitHub-based setup if available
- Add the token in GitHub repo: ➔ GitHub → Settings → Secrets and variables → Actions → New Repository Secret:
  -   Name: SONAR_TOKEN
  -   value: your generated token
  -   Name: SONAR_HOST_URL
  -   value: use https://your-sonarqube-server.com if using SonarQube or else use https://sonarcloud.io for SonarCloud
- Create a file called sonar-project.properties and keep it in root of project:
  ```bash
    sonar.projectKey=<YOUR_PROJECT_KEY>
    sonar.organization=<YOUR_ORG_NAME> // (only for SonarCloud)
    sonar.host.url=https://sonarcloud.io
    sonar.sources=.
    sonar.language=js
  ```
  This tells SonarScanner how to scan your project.
- Add GitHub Action Workflow (.github/workflows/sonarcloud.yml): code is provided in the Repo.

## ⚡ Custom Quality Gates
- In SonarCloud UI → Go to your project → Administration → Quality Gates → create your own rules, like:
    - Coverage > 80%
    - 0 Bugs
    - 0 Critical Security Hotspots
- Your PRs will only pass if they meet this standard!

## 🔥 How does it work?
- Whenever your code is pushed or a PR is created, GitHub Action runs, SonarQube scanner checks your code and update SonarQube dashboard with report

## 📦 Installation

```bash
# Clone the repo
git clone https://github.com/rupachowrasia/nodejs-sonarcloud-setup-with-github-action.git

# Move into the project directory
cd nodejs-sonarcloud-setup-with-github-action

# Install dependencies
npm install

# Run the app
npm run start
