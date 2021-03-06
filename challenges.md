## Challenge:
After running 

`docker run -it jenkins/jnlp-slave -url http://localhost:8080 <secret-key> agent-pimento`

I got error:

	SEVERE: Failed to connect to http://localhost:8080/tcpSlaveAgentListener/: Connection refused (Connection refused)
	java.io.IOException: Failed to connect to http://localhost:8080/tcpSlaveAgentListener/: Connection refused (Connection refused)```

## Solution:
This was corrected by using the IP address rather than just localhost.

## Challenge:

Running pipeline job on Java agent works successfully (see [java-agent.md](java-agent.md)). 

	Running the job on the docker jnlp-slave agent fails with:
	Started by user admin
	Running in Durability level: MAX_SURVIVABILITY
	[Pipeline] Start of Pipeline
	[Pipeline] node
	Running on agent-pimento in /var/jenkins/agent-pimento/workspace/agent-pimento-job
	[Pipeline] {
	[Pipeline] stage
	[Pipeline] { (Build image)
	[Pipeline] isUnix
	[Pipeline] sh
	[Pipeline] }
	[Pipeline] // stage
	[Pipeline] }
	[Pipeline] // node
	[Pipeline] End of Pipeline
	Also:   hudson.remoting.Channel$CallSiteStackTrace: Remote call to JNLP4-connect connection from 172.17.0.1/172.17.0.1:36046
			at hudson.remoting.Channel.attachCallSiteStackTrace(Channel.java:1741)
			at hudson.remoting.UserRequest$ExceptionResponse.retrieve(UserRequest.java:356)
			at hudson.remoting.Channel.call(Channel.java:955)
			at hudson.FilePath.act(FilePath.java:1069)
			at hudson.FilePath.act(FilePath.java:1058)
			at hudson.FilePath.mkdirs(FilePath.java:1243)
			at org.jenkinsci.plugins.durabletask.FileMonitoringTask$FileMonitoringController.<init>(FileMonitoringTask.java:181)
			at org.jenkinsci.plugins.durabletask.BourneShellScript$ShellController.<init>(BourneShellScript.java:332)
			at org.jenkinsci.plugins.durabletask.BourneShellScript$ShellController.<init>(BourneShellScript.java:321)
			at org.jenkinsci.plugins.durabletask.BourneShellScript.launchWithCookie(BourneShellScript.java:177)
			at org.jenkinsci.plugins.durabletask.FileMonitoringTask.launch(FileMonitoringTask.java:99)
			at org.jenkinsci.plugins.workflow.steps.durable_task.DurableTaskStep$Execution.start(DurableTaskStep.java:317)
			at org.jenkinsci.plugins.workflow.cps.DSL.invokeStep(DSL.java:286)
			at org.jenkinsci.plugins.workflow.cps.DSL.invokeMethod(DSL.java:179)
			at org.jenkinsci.plugins.workflow.cps.CpsScript.invokeMethod(CpsScript.java:122)
			at org.codehaus.groovy.runtime.callsite.PogoMetaClassSite.call(PogoMetaClassSite.java:48)
			at org.codehaus.groovy.runtime.callsite.CallSiteArray.defaultCall(CallSiteArray.java:48)
			at org.codehaus.groovy.runtime.callsite.AbstractCallSite.call(AbstractCallSite.java:113)
			at com.cloudbees.groovy.cps.sandbox.DefaultInvoker.methodCall(DefaultInvoker.java:20)
			at com.cloudbees.groovy.cps.impl.ContinuationGroup.methodCall(ContinuationGroup.java:86)
			at com.cloudbees.groovy.cps.impl.FunctionCallBlock$ContinuationImpl.dispatchOrArg(FunctionCallBlock.java:113)
			at com.cloudbees.groovy.cps.impl.FunctionCallBlock$ContinuationImpl.fixArg(FunctionCallBlock.java:83)
			at sun.reflect.GeneratedMethodAccessor243.invoke(Unknown Source)
			at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
			at java.lang.reflect.Method.invoke(Method.java:498)
			at com.cloudbees.groovy.cps.impl.ContinuationPtr$ContinuationImpl.receive(ContinuationPtr.java:72)
			at com.cloudbees.groovy.cps.impl.CollectionLiteralBlock$ContinuationImpl.dispatch(CollectionLiteralBlock.java:55)
			at com.cloudbees.groovy.cps.impl.CollectionLiteralBlock$ContinuationImpl.item(CollectionLiteralBlock.java:45)
			at sun.reflect.GeneratedMethodAccessor247.invoke(Unknown Source)
			at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
			at java.lang.reflect.Method.invoke(Method.java:498)
			at com.cloudbees.groovy.cps.impl.ContinuationPtr$ContinuationImpl.receive(ContinuationPtr.java:72)
			at com.cloudbees.groovy.cps.impl.ConstantBlock.eval(ConstantBlock.java:21)
			at com.cloudbees.groovy.cps.Next.step(Next.java:83)
			at com.cloudbees.groovy.cps.Continuable$1.call(Continuable.java:174)
			at com.cloudbees.groovy.cps.Continuable$1.call(Continuable.java:163)
			at org.codehaus.groovy.runtime.GroovyCategorySupport$ThreadCategoryInfo.use(GroovyCategorySupport.java:129)
			at org.codehaus.groovy.runtime.GroovyCategorySupport.use(GroovyCategorySupport.java:268)
			at com.cloudbees.groovy.cps.Continuable.run0(Continuable.java:163)
			at org.jenkinsci.plugins.workflow.cps.SandboxContinuable.access$001(SandboxContinuable.java:18)
			at org.jenkinsci.plugins.workflow.cps.SandboxContinuable.run0(SandboxContinuable.java:51)
			at org.jenkinsci.plugins.workflow.cps.CpsThread.runNextChunk(CpsThread.java:185)
			at org.jenkinsci.plugins.workflow.cps.CpsThreadGroup.run(CpsThreadGroup.java:400)
			at org.jenkinsci.plugins.workflow.cps.CpsThreadGroup.access$400(CpsThreadGroup.java:96)
			at org.jenkinsci.plugins.workflow.cps.CpsThreadGroup$2.call(CpsThreadGroup.java:312)
			at org.jenkinsci.plugins.workflow.cps.CpsThreadGroup$2.call(CpsThreadGroup.java:276)
			at org.jenkinsci.plugins.workflow.cps.CpsVmExecutorService$2.call(CpsVmExecutorService.java:67)
			at java.util.concurrent.FutureTask.run(FutureTask.java:266)
			at hudson.remoting.SingleLaneExecutorService$1.run(SingleLaneExecutorService.java:131)
			at jenkins.util.ContextResettingExecutorService$1.run(ContextResettingExecutorService.java:28)
			at jenkins.security.ImpersonatingExecutorService$1.run(ImpersonatingExecutorService.java:59)
			at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
			at java.util.concurrent.FutureTask.run(FutureTask.java:266)
			at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)
			at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)
	java.nio.file.AccessDeniedException: /var/jenkins
		at sun.nio.fs.UnixException.translateToIOException(UnixException.java:84)
		at sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:102)
		at sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:107)
		at sun.nio.fs.UnixFileSystemProvider.createDirectory(UnixFileSystemProvider.java:384)
		at java.nio.file.Files.createDirectory(Files.java:674)
		at java.nio.file.Files.createAndCheckIsDirectory(Files.java:781)
		at java.nio.file.Files.createDirectories(Files.java:767)
		at hudson.FilePath.mkdirs(FilePath.java:3256)
		at hudson.FilePath.access$1300(FilePath.java:211)
		at hudson.FilePath$Mkdirs.invoke(FilePath.java:1251)
		at hudson.FilePath$Mkdirs.invoke(FilePath.java:1247)
		at hudson.FilePath$FileCallableWrapper.call(FilePath.java:3069)
		at hudson.remoting.UserRequest.perform(UserRequest.java:211)
		at hudson.remoting.UserRequest.perform(UserRequest.java:54)
		at hudson.remoting.Request$2.run(Request.java:369)
		at hudson.remoting.InterceptingExecutorService$1.call(InterceptingExecutorService.java:72)
		at java.util.concurrent.FutureTask.run(FutureTask.java:266)
		at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)
		at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)
		at hudson.remoting.Engine$1.lambda$newThread$0(Engine.java:117)
		at java.lang.Thread.run(Thread.java:748)
	Finished: FAILURE

## Investigations
I have a user `jenkins` with permission in the `docker` group
	
	cat /etc/group | grep 'docker'
	docker:x:999:jenkins

I have given permission to user `jenkins` and the `docker` group to read and write to the folder and it's child folders 
	
	ls -lna /var/jenkins_home/
	total 20
	drwxr-xr-x  4 1000 999 4096 Mar  2 19:44 .
	drwxr-xr-x 15    0   0 4096 Mar  2 04:57 ..
	-rw-r--r--  1 1000 999  161 Feb 29 01:54 Dockerfile
	drwxr-xr-x  2 1000 999 4096 Mar  2 19:44 agent-pimento
	drwxr-xr-x  5 1000 999 4096 Mar  2 18:26 pimento2

Doing `docker run --user jenkins jenkins/jnlp-slave -url http://167.99.106.130:8080 b3c5f07d3eb2124ee7f30b164c7df3ed8f69c38ca7d1cf97750db430629caf50 -workDir="/var/jenkins_home/agent-pimento" agent-pimento`

Results in the specific access denied error.

	Mar 02, 2020 7:53:00 PM hudson.remoting.jnlp.Main createEngine
	INFO: Setting up agent: agent-pimento
	Mar 02, 2020 7:53:00 PM hudson.remoting.jnlp.Main$CuiListener <init>
	INFO: Jenkins agent is running in headless mode.
	Mar 02, 2020 7:53:00 PM hudson.remoting.Engine startEngine
	INFO: Using Remoting version: 4.0.1
	Exception in thread "main" java.nio.file.AccessDeniedException: /var/jenkins_home

Chmod /jenkins_home in the host container and then start the agent container again.
Chmod /jenkins_home (the mounted volume when starting the agent container) by entering the agent container  

`docker exec -it -u root <container id> bash`

## Solution
With Aaron's help, I realized I was mounting a volume to a path on the agent rather than keeping the path the same between both. After changing the mounting parameter, I could find the problematic folder. Just to verify that it's a permission issue with the folder on the agent. I changed the permissions to 777 for testing. I'd want to find a better solution as that's not secure.

## Challenge
Docker not found

## Solution
Added Docker in global tool configuration. In the ned, I went with the docker path bindmounting and docker unix socket bindmounting instead of using the global tool configuration with an initialization stage.

## Challenge
When trying to pull Docker image 
	
	Warning: failed to get default registry endpoint from daemon (Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?). Using system default: https://index.docker.io/v1/

	Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?

## Investigation
Tried re-running master container and bindmounting the Docker Unix socket  
`-v /var/run/docker.sock:/var/run/docker.sock`

Bindmounting docker path as well and unix socket in the master container. Bindmount the unix socket in the master container and install docker using dockerfile to build custom image based on jenkins/jnlp-slave.

## Solution
Build image for agent with docker using [Dockerfile.jnlp](Dockerfile.jnlp) because I got tired of rerunning commands. Run master container with bindmounting for docker path and docker unix socket. Run agent container with bindmounting for docker unix socket. This took some docker exec'ing to start the docker service.
