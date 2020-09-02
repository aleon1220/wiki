# jenkins
jenkins.io

### example of using startup flags
```
java -Dhudson.footerURL=http://example.org -jar jenkins.war \
--httpPort=8083 --prefix=/ci --httpListenAddress=127.0.0.1
```

Setting the Java system property (JAVA_OPTS) `-Dhudson.footerURL=http://example.org` will change the default footer on the Jenkins UI to http://example.com
`--httpPort`, `--prefix`, and `--httpListenAddress` are the flags provided as JENKINS_OPTS
`--httpPort=8083` will set the Jenkins port to 8083 instead of the default 8080
`--prefix=/ci` will add a prefix to the end of the Jenkins URL
`--httpListenAddress=127.0.0.1` binds Jenkins to the IP address.

[Jenkins Features Controlled with System Properties](https://jenkins.io/doc/book/managing/system-properties/)

 Jenkins settings file= `/etc/default/jenkins`
 startup script= `/etc/init.d/jenkins`
 Jenkins home directory= `/var/lib/jenkins`
 Jenkins log file= `/var/log/jenkins`

## Jenkins Docker Container
https://hub.docker.com/r/jenkins/jenkins/
[Run Jenkins in Docker Container](https://www.jenkins.io/doc/book/installing/#downloading-and-running-jenkins-in-docker)

# Jenkins Kubernetes Helm Chart
[Helm chart for Jenkins](https://github.com/helm/charts/tree/master/stable/jenkins)

## Jenkins Glossary
see [jenkins.io book](https://www.jenkins.io/doc/book/glossary/)

### Distributed Builds Terminology
From [EDX Jenkins](https://learning.edx.org/course/course-v1:LinuxFoundationX+LFS167x+2T2020/block-v1:LinuxFoundationX+LFS167x+2T2020+type@sequential+block@6074ebbee1a94de5963c3dbe2d021d4c/block-v1:LinuxFoundationX+LFS167x+2T2020+type@vertical+block@99c7f23e787749e4bb1734ee825be29a)
Before we deep dive into distributed build architecture, let’s quickly review some terminology related it.

Master= A machine where Jenkins is installed. It centrally stores all the configurations, loads plugins and renders the Jenkins UI.
Agent= A machine which connects to the Jenkins master and performs various operations as directed by the Jenkins master.
Node= A machine that can allocate an executor and run Jenkins Pipelines. Examples are Jenkins masters and Agents. You will notice that nodes and agents are sometimes used synonymously.
Executor= A Jenkins executor is one of the basic building blocks which allows a build to run on a node. You can configure more than one executor for every node. The number of executors is set based on the number of CPUs, IO performance and other hardware characteristics of a node and the type of builds you have configured to run. The number of executors determines the number of concurrent builds that can be run at any given point in time.

It is Jenkins security best practice to set the number of executors to 0 on the Jenkins master, and not run any builds on it.

## Plugins used up to this point 2020
- [Blue Ocean](https://plugins.jenkins.io/blueocean/) graphical editor = Easily create your Jenkinsfile and define pipelines execution.
- [Docker](https://plugins.jenkins.io/docker-plugin/) = Interacts with Docker
- [JaCoCo plugin](https://plugins.jenkins.io/jacoco/) = Java Code Coverage
- [Warnings Next Generation](https://plugins.jenkins.io/warnings-ng/) = Collects compiler warnings or issues reported by static analysis tools and visualizes the results.
- Folders = helps in organizing the structure of projects
- Prometheus metrics(https://plugins.jenkins.io/prometheus/#documentation)
- Docker(https://plugins.jenkins.io/docker-plugin/) = Jenkins cloud plugin for docker
- Kubernetes(https://plugins.jenkins.io/kubernetes/) = Run dynamic agents in Kubernetes