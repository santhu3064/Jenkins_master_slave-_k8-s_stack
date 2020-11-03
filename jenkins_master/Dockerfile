FROM jenkins/jenkins:lts

RUN mkdir /var/jenkins_home/casc_configs \
&& chown -R jenkins:jenkins /var/jenkins_home/casc_configs

ADD plugins.txt /usr/share/jenkins/ref/plugins.txt

RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt
