Running agent using Docker agent:

pipeline job:
	node('blah') {
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
	Running on blah in /jenkins_home/workspace/bahhhhh
	[Pipeline] {
	[Pipeline] stage
	[Pipeline] { (Build image)
	[Pipeline] isUnix
	[Pipeline] sh
	+ docker inspect -f . node:6.3
	.
	[Pipeline] withDockerContainer
	blah seems to be running inside container 8bcecb13f2944fe3e561c04de51afd1c5b448f95e733a0b94cbc3a862814afa2
	$ docker run -t -d -u 1000:1000 -w /jenkins_home/workspace/bahhhhh --volumes-from 8bcecb13f2944fe3e561c04de51afd1c5b448f95e733a0b94cbc3a862814afa2 -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** -e ******** node:6.3 cat
	$ docker top 7a6c46530fcc67a58121609b2fda7568b69aa950602e2f7ffd52238b5548d759 -eo pid,comm
	[Pipeline] {
	[Pipeline] sh
	+ npm --version
	3.10.3
	[Pipeline] }
	$ docker stop --time=1 7a6c46530fcc67a58121609b2fda7568b69aa950602e2f7ffd52238b5548d759
	$ docker rm -f 7a6c46530fcc67a58121609b2fda7568b69aa950602e2f7ffd52238b5548d759
	[Pipeline] // withDockerContainer
	[Pipeline] }
	[Pipeline] // stage
	[Pipeline] }
	[Pipeline] // node
	[Pipeline] End of Pipeline
	Finished: SUCCESS