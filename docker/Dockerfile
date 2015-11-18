FROM ubuntu:14.04
MAINTAINER longlx &lt;longlx@septeni-technology.jp&gt;;

# Create play user, group
RUN groupadd play
RUN useradd play -m -g play -s /bin/bash
RUN passwd -d -u play
RUN echo "play ALL=(ALL) NOPASSWD:ALL" &gt; /etc/sudoers.d/play
RUN chmod 0440 /etc/sudoers.d/play

# Install dependencies
RUN apt-get update
RUN apt-get install -y git build-essential curl
RUN apt-get install -y wget
RUN apt-get install -y zip unzip

# Install play
WORKDIR /tmp
RUN wget http://downloads.typesafe.com/play/2.2.6/play-2.2.6.zip
RUN unzip play-2.2.6.zip
RUN mv play-2.2.6 /home/play/play

# Install jdk, openjdk
RUN apt-get install -y default-jdk openjdk-7-jre

# Expose play framwork port 9000
EXPOSE 9000
CMD cd /home/play/play/samples/scala/helloworld &amp;&amp; /home/play/play/play run