FROM jenkins/jenkins:latest

RUN /usr/local/bin/install-plugins.sh git mstest matrix-auth workflow-aggregator docker-workflow blueocean credentials-binding

ENV JENKINS_USER demo
ENV JENKINS_PASS admin123

RUN /usr/local/bin/install-plugins.sh greenballs
# Skip initial setup
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

COPY executors.groovy /usr/share/jenkins/ref/init.groovy.d/
COPY default-user.groovy /usr/share/jenkins/ref/init.groovy.d/

VOLUME /var/jenkins_home
