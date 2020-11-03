ARG version=4.3-8
FROM jenkins/agent:$version


ARG version
LABEL Description="This is a base image, which allows connecting Jenkins agents via JNLP protocols" Vendor="Jenkins project" Version="$version"

ARG user=jenkins
ARG npm_version=12

USER root

RUN curl -sL https://deb.nodesource.com/setup_12.x
RUN apt-get update -y \
&& apt-get install nodejs  -y \
&& rm -rf /var/lib/apt/lists/*


RUN curl -L https://npmjs.org/install.sh -o install.sh \
&& sh install.sh

COPY jenkins-agent /usr/local/bin/jenkins-agent
RUN chmod +x /usr/local/bin/jenkins-agent &&\
    ln -s /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-slave
USER ${user}


ENTRYPOINT ["jenkins-agent"]
