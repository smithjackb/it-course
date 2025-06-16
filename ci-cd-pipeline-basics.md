# CI/CD Pipeline Basics using GitHub Actions or Jenkins

Continuous Integration and Continuous Deployment (CI/CD) help automate the software delivery process. This guide walks you through **step-by-step** setup of basic CI/CD pipelines using **GitHub Actions** and **Jenkins**.

---

## What is CI/CD?

- **Continuous Integration (CI):** Automatically build and test your code every time you push changes.
- **Continuous Deployment (CD):** Automatically deploy your code to an environment after successful tests.

---

# Step-by-Step: CI/CD with GitHub Actions

GitHub Actions is built directly into GitHub and uses YAML files to define workflows.

### Step 1: Create your GitHub repository
- Go to GitHub and create a new repository or use an existing one.

### Step 2: Create a workflow file
- Inside your repo, create a folder called `.github/workflows`.
- Inside this folder, create a file named `ci.yml` (or any name ending with `.yml`).

### Step 3: Define the workflow
- Add the following content to `ci.yml`:

```yaml
name: CI Pipeline

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Set up Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '16'

    - name: Install dependencies
      run: npm install

    - name: Run tests
      run: npm test

    - name: Build
      run: npm run build
````

### Step 4: Commit and push your changes

* Commit the new workflow file and push it to your repo.
* GitHub will automatically trigger the workflow on every push or pull request to `main`.

### Step 5: View the workflow run

* Go to the **Actions** tab in your GitHub repo.
* You can see the status of your CI pipeline and detailed logs.

---

# Step-by-Step: CI/CD with Jenkins

Jenkins requires a server (local or cloud) to run your pipelines.

### Step 1: Install Jenkins

* Download and install Jenkins from [https://jenkins.io](https://jenkins.io).
* Start Jenkins and complete the initial setup.

### Step 2: Create a new Jenkins pipeline job

* Log in to Jenkins.
* Click **New Item**, enter a name, and select **Pipeline**.

### Step 3: Create a `Jenkinsfile` in your repo

* In your project repository, add a file named `Jenkinsfile` with the following content:

```groovy
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add your deployment script here
            }
        }
    }
    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
```

### Step 4: Configure Jenkins to use your repo

* In the Jenkins job configuration, under **Pipeline**, set:

  * Definition: Pipeline script from SCM
  * SCM: Git
  * Repository URL: your repo URL

### Step 5: Run the pipeline

* Save the job configuration.
* Click **Build Now** to run the pipeline.
* Monitor the pipeline logs on the Jenkins dashboard.

---

# Summary

| Step                | GitHub Actions                   | Jenkins                         |
| ------------------- | -------------------------------- | ------------------------------- |
| Setup               | Create `.github/workflows/*.yml` | Install Jenkins and create job  |
| Pipeline definition | YAML in repo                     | Jenkinsfile in repo             |
| Trigger             | On git events (push, PR)         | Manual or webhook triggers      |
| Build & Test        | Automatic steps in workflow      | Stages in Jenkinsfile           |
| Deployment          | Add deployment step in workflow  | Add deploy stage in Jenkinsfile |

---

# Final Tips

* Start simple: first automate builds and tests.
* Add deployment once your pipeline runs reliably.
* Use secrets and environment variables securely.
* Explore marketplace actions or Jenkins plugins to extend functionality.

---

If this guide helped, please ⭐ star the repo and share your thoughts!

---

*Happy coding!* 🚀

```

