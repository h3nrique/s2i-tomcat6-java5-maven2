# S2I Tomcat6 Java5 Maven2

S2I Image Builder for building with Maven2 and running Java 5 applications on Tomcat 6.

First Step
---
Before you build this image, it's necessary [download Java 5](https://www.oracle.com/java/technologies/java-archive-javase5-downloads.html) installer file (jdk-1_5_0_22-linux-amd64.bin), put on java-installer directory and create sha256 file (user command `sha256sum jdk-1_5_0_22-linux-amd64.bin > jdk-1_5_0_22-linux-amd64.bin.sha256`).

Local Docker build
---
```bash
$ docker build -t h3nrique/s2i-tomcat6-java5-maven2:latest .
```

Local Test
---
```bash
$ s2i build https://github.com/h3nrique/systemprops.git h3nrique/s2i-tomcat6-java5-maven2:latest demoapp -e WAR_NAME=systemprops.war
$ docker run -p 8080:8080 demoapp
```

Deploy Builder on Openshift
---
```bash
$ oc new-build "https://github.com/h3nrique/s2i-tomcat6-java5-maven2.git" --name=s2i-tomcat6-java5-maven2--strategy=docker
```
