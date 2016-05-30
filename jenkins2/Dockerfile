From tomcat:7-jre8
ADD jenkins.war /usr/local/tomcat/webapps/

RUN mkdir -p /var/jenkinsHome && mkdir -p /var/workspace
VOLUME /var/workspace
VOLUME /var/jenkinsHome
WORKDIR /var/jenkinsHome
ENV JENKINS_HOME /var/jenkinsHome
