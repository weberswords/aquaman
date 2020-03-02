Running agent using Java command:

pipeline job:

	node('pimento-2') {
	    stage('Build image') {
	        docker.image('node:6.3').inside {
	            sh 'npm --version'
	        }
	    }
	}

output:
	
	Started by user admin
	Running in Durability level: MAX_SURVIVABILITY
	[Pipeline] Start of Pipeline
	[Pipeline] node
	Running on pimento-2 in /var/jenkins_home/pimento2/workspace/pimento2-job
	[Pipeline] {
	[Pipeline] stage
	[Pipeline] { (Build image)
	[Pipeline] isUnix
	[Pipeline] sh
	+ docker inspect -f . node:6.3

	Error: No such object: node:6.3
	[Pipeline] isUnix
	[Pipeline] sh
	+ docker pull node:6.3
	6.3: Pulling from library/node
	357ea8c3d80b: Pulling fs layer
	52befadefd24: Pulling fs layer
	3c0732d5313c: Pulling fs layer
	ceb711c7e301: Pulling fs layer
	868b1d0e2aad: Pulling fs layer
	646e6da4bf07: Pulling fs layer
	ceb711c7e301: Waiting
	868b1d0e2aad: Waiting
	646e6da4bf07: Waiting
	52befadefd24: Verifying Checksum
	52befadefd24: Download complete
	3c0732d5313c: Verifying Checksum
	3c0732d5313c: Download complete
	357ea8c3d80b: Verifying Checksum
	357ea8c3d80b: Download complete
	868b1d0e2aad: Verifying Checksum
	868b1d0e2aad: Download complete
	646e6da4bf07: Verifying Checksum
	646e6da4bf07: Download complete
	ceb711c7e301: Verifying Checksum
	ceb711c7e301: Download complete
	357ea8c3d80b: Pull complete
	52befadefd24: Pull complete
	3c0732d5313c: Pull complete
	ceb711c7e301: Pull complete
	868b1d0e2aad: Pull complete
	646e6da4bf07: Pull complete
	Digest: sha256:cde2bd38dbfec5e6e2981ec7a05056c734148fcd4bff088e143f11b2bafe3b64
	Status: Downloaded newer image for node:6.3
	docker.io/library/node:6.3
	[Pipeline] withDockerContainer
	pimento-2 does not seem to be running inside a container
	$ docker run -t -d -u 0:0 -w /var/jenkins_home/pimento2/workspace/pimento2-job -v /var/jenkins_home/pimento2/workspace/pimento2-job:/var/jenkins_home/pimento2/workspace/pimento2-job:rw,z -v /var/jenkins_home/pimento2/workspace/pimento2-job@tmp:/var/jenkins_home/pimento2/workspace/pimento2-job@tmp:rw,z -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** node:6.3 cat
	$ docker top 4a72cd5b13a840ac377df7d157bc0d32d6abcda9ef65df3e65aa38e00b392c9d -eo pid,comm
	[Pipeline] {
	[Pipeline] sh
	+ npm --version
	3.10.3
	[Pipeline] }
	$ docker stop --time=1 4a72cd5b13a840ac377df7d157bc0d32d6abcda9ef65df3e65aa38e00b392c9d
	$ docker rm -f 4a72cd5b13a840ac377df7d157bc0d32d6abcda9ef65df3e65aa38e00b392c9d
	[Pipeline] // withDockerContainer
	[Pipeline] }
	[Pipeline] // stage
	[Pipeline] }
	[Pipeline] // node
	[Pipeline] End of Pipeline
	Finished: SUCCESS