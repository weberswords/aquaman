1. On any Linux hosts that doesn't have docker, install Docker. Recommend to use Ubuntu (I'm using ubuntu:18.04). 
2. Run Jenkins [Master] and a Jenkins agent containers - both can be found in Docker Hub. 
(Note, use jenkins/jenkins:lts for the master due to plugin issues if you use the latest, jenkins/jnlp-slave for the agent.)
3. Create a Jenkins Pipeline that builds a Docker image (any image) from the Jenkins Agent, jnlp-slave.
4. Run the pipeline task and see that the image was created.
5. Send a summary of what you did and the [challenges](challenges.md) you faced including: 

A. Docker run commands for both containers
- Master:
	`docker run -p 8080:8080 -p 50000:50000 -v /jenkins_home -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker jenkins/jenkins:lts`

- Agent:
	`docker run -it -v /jenkins_home -v /var/run/docker.sock:/var/run/docker.sock <custom image from dockerfile.jnlp> -url http://<host ip>:8080 <agent secret> <agent-name>`

B. Docker [image output showing the image created](docker-agent.md)

Note: the Dockerfile.jnlp was adapted from [this](https://medium.com/@prashant.vats/jenkins-master-and-slave-with-docker-b993dd031cbd) combined with my trial and error installing docker on the jnlp-agent node.
