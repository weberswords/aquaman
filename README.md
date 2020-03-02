1. On any Linux hosts that doesn't have docker, install Docker. Recommend to use Ubuntu (I'm using ubuntu:18.04). 
2. Run Jenkins [Master] and a Jenkins agent containers - both can be found in Docker Hub. 
(Note, use jenkins/jenkins:lts for the master due to plugin issues if you use the latest, jenkins/jnlp-slave for the agent.)
3. Create a Jenkins Pipeline that builds a Docker image (any image) from the Jenkins Agent, jnlp-slave.
4. Run the pipeline task and see that the image was created.
5. Send a summary of what you did and the [challenges](challenges.md) you faced including: 

A. Docker run commands for both containers
- Master:
	`docker run -d -p 8080:8080 -p 50000:50000 -v /var/jenkins_home jenkins/jenkins:lts`

- Agent:
	`docker run -dit jenkins/jnlp-slave -url http://<ip address>:8080 <secret key from master> agent-pimento` 

B. Docker image output showing the image created 
