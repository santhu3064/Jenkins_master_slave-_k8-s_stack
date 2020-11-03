ARG version=4.3-8
FROM jenkins/agent:$version

ARG version
LABEL Description="This is a base image, which allows connecting Jenkins agents via JNLP protocols" Vendor="Jenkins project" Version="$version"

ARG user=jenkins

USER root

WORKDIR /opt
RUN curl https://apache.mirrors.nublue.co.uk/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz -o  apache-maven-3.6.3.tar.gz \
&& tar -xvzf apache-maven-3.6.3.tar.gz

ENV PATH="/opt/apache-maven-3.6.3/bin:$PATH"

RUN  mvn -v

COPY jenkins-agent /usr/local/bin/jenkins-agent
RUN chmod +x /usr/local/bin/jenkins-agent &&\
    ln -s /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-slave
USER ${user}


ENTRYPOINT ["jenkins-agent"]
