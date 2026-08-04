Experiment 4 — Jenkins CI Pipeline 

Goal
Set up Jenkins on a cloud server and create a pipeline that automatically pulls code from GitHub, builds it, and tests it.

Environment
Server: AWS EC2 instance (Ubuntu), IP fixed with an Elastic IP: 13.232.43.123
Jenkins: running at http://13.232.43.123:8080
Code: Java + Maven project, hosted at https://github.com/daarani24/DevOps_Lab.git

Steps performed
Launched an EC2 instance (Ubuntu) on AWS.
Opened port 8080 in the instance's Security Group (needed so Jenkins is reachable from a browser).
Installed Java (openjdk-21-jre) — Jenkins needs Java to run.
Installed Jenkins using its official apt repository, then started it as a service (sudo systemctl start jenkins).
Unlocked Jenkins using the initial admin password, installed suggested plugins, created an admin login.
Configured tools in Jenkins (Manage Jenkins → Tools): added JDK and Maven installations.
Created a Pipeline job (CI-Pipeline) and wrote a Jenkinsfile with 3 stages:
  Checkout — pulls the latest code from the GitHub repo.
  Build — runs mvn clean compile to compile the Java code.
  Test — runs mvn test to run the automated test suite.
Ran the pipeline (Build Now) — watched it succeed in Console Output.
Attached an Elastic IP to the EC2 instance so the IP stops changing on restarts.

Pipeline Workflow
Developer
      │
      ▼
Push Code to GitHub
      │
      ▼
Jenkins Pipeline
      │
      ▼
Checkout Source Code
      │
      ▼
Build (Maven)
      │
      ▼
Run Tests
      │
      ▼
Build Success

Result
Jenkins successfully pulls the project from GitHub, compiles it with Maven, and runs its tests automatically — a working CI pipeline.
