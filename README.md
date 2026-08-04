# Experiment 4 — Jenkins CI Pipeline
 
## Goal
Set up Jenkins on a cloud server and create a pipeline that automatically pulls code from GitHub, builds it, and tests it.
 
## Environment
- **Server:** AWS EC2 instance (Ubuntu), IP fixed with an Elastic IP: `13.232.43.123`
- **Jenkins:** running at `http://13.232.43.123:8080`
- **Code:** Java + Maven project, hosted at `https://github.com/daarani24/DevOps_Lab.git`
  
## Steps performed
1. **Launched an EC2 instance** (Ubuntu) on AWS.
2. **Opened port 8080** in the instance's Security Group (needed so Jenkins is reachable from a browser).
3. **Installed Java** (`openjdk-21-jre`) — Jenkins needs Java to run.
4. **Installed Jenkins** using its official apt repository, then started it as a service (`sudo systemctl start jenkins`).
5. **Unlocked Jenkins** using the initial admin password, installed suggested plugins, created an admin login.
6. **Configured tools** in Jenkins (Manage Jenkins → Tools): added JDK and Maven installations.
7. **Created a Pipeline job** (`CI-Pipeline`) and wrote a Jenkinsfile with 3 stages:
   - **Checkout** — pulls the latest code from the GitHub repo.
   - **Build** — runs `mvn clean compile` to compile the Java code.
   - **Test** — runs `mvn test` to run the automated test suite.
8. **Ran the pipeline** (Build Now) — watched it succeed in Console Output.
9. **Attached an Elastic IP** to the EC2 instance so the IP stops changing on restarts.
    
## Result
Jenkins successfully pulls the project from GitHub, compiles it with Maven, and runs its tests automatically — a working CI pipeline.
