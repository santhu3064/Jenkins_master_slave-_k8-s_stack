FROM jenkins/jenkins:lts
ARG user=jenkins
ARG ansible_version=2.9.4

RUN mkdir /var/jenkins_home/casc_configs \
&& chown -R jenkins:jenkins /var/jenkins_home/casc_configs

USER root
WORKDIR /opt
RUN curl https://apache.mirrors.nublue.co.uk/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz -o  apache-maven-3.6.3.tar.gz \
&& tar -xvzf apache-maven-3.6.3.tar.gz

ENV PATH="/opt/apache-maven-3.6.3/bin:$PATH"

RUN  mvn -v


USER $user
ADD plugins.txt /usr/share/jenkins/ref/plugins.txt

RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt
