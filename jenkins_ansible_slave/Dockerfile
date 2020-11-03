ARG version=4.3-8
FROM jenkins/agent:$version


ARG version
LABEL Description="This is a base image, which allows connecting Jenkins agents via JNLP protocols" Vendor="Jenkins project" Version="$version"

ARG user=jenkins
ARG ansible_version=2.9.4

USER root

RUN apt-get update -y \
&& apt-get install python3  python3-distutils -y \
&& rm -rf /var/lib/apt/lists/*


RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py \
&& python3 get-pip.py \
&& pip3 install ansible==${ansible_version}

COPY jenkins-agent /usr/local/bin/jenkins-agent
RUN chmod +x /usr/local/bin/jenkins-agent &&\
    ln -s /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-slave
USER ${user}


ENTRYPOINT ["jenkins-agent"]
