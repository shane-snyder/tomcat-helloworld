# tomcat-helloworld
This is an example to deploy a basic hello world tomcat application using JBoss Webserver 5.7 builder image. This uses an existing war file.

- [Docs](https://access.redhat.com/documentation/en-us/red_hat_jboss_web_server/6.0/html-single/red_hat_jboss_web_server_for_openshift/index#Create-an-OpenShift-application-using-existing-maven-binaries)
- [Image](https://catalog.redhat.com/software/containers/jboss-webserver-5/jws57-openjdk8-openshift-rhel8/6231b7d3f506970211844711?architecture=amd64&image=65e73f1f4a4799a06847e2d0)
## Commands

```
oc project default
oc new-build --binary=true --image-stream=jboss-webserver57-openjdk8-tomcat9-openshift-ubi8:latest --name=jws-wsch-app
oc start-build jws-wsch-app --from-dir=./ocp --follow
oc new-app jws-wsch-app
oc expose service/jws-wsch-app
```