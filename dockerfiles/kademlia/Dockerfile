############################################################
# Dockerfile to build kademlia container image
# Based on Ubuntu
############################################################

# Set the base image to Ubuntu
FROM ubuntu

# File Author / Maintainer
MAINTAINER Muneeb Ali (@muneeb)

# Update the repository sources list
RUN apt-get dist-upgrade

################## BEGIN INSTALLATION ######################

# Add the package verification key
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10

# Update the repository sources list once more
RUN apt-get update
RUN apt-get -y upgrade

# Install packages
RUN apt-get install -y git
RUN apt-get install -y python-pip
RUN apt-get install -y python-dev

# Create the default directory
RUN mkdir -p /srv/kademlia

# Clone the app from github and install packages
RUN git clone https://github.com/openname/kademlia.git /srv/kademlia
RUN pip install kademlia 

##################### INSTALLATION END #####################

# Expose the default port
EXPOSE 8468

# Set default container command
ENTRYPOINT /usr/local/bin/twistd -noy /srv/kademlia/examples/server.tac