FROM centos:latest

# Install packages
RUN yum -y update &&  yum clean all
RUN yum -y install epel-release && yum clean all
RUN yum install -y vi
RUN yum -y install cronie
RUN yum -y install mysql

ADD fetch/start.sh /start.sh
RUN chmod 755 /start.sh

# Add crontab file in the cron directory
ADD fetch/crontab /etc/cron.d/ultipro-cron
ADD fetch/my-cron.conf /etc/cron.d/my-cron

# Give execution rights on the cron job
RUN chmod 0644 /etc/cron.d/ultipro-cron
RUN chmod 0644 /etc/cron.d/my-cron

ENV HOME "/root"

# Set JAVA_HOME
ENV JAVA_HOME $HOME/ultipro/jre1.8.0_161

# Create environment variable file to access from cron job
RUN env > $HOME/container.env

# Create folders to place jars
RUN mkdir -p $HOME/ultipro
RUN mkdir -p $HOME/ultipro/ultipro-download

# Set work dir
WORKDIR $HOME/ultipro

# Copy property file 
COPY fetch/ultipro-job.properties $HOME/ultipro/

# Copy JRE to container
ADD ./jre-8u161-linux-x64.tar.gz $HOME/ultipro/

# Copy jar relavant folders
COPY fetch/ultipro-download/fetch.jar $HOME/ultipro/ultipro-download/fetch.jar

CMD ["/bin/bash", "/start.sh"]
