##
# Base image for development on Ubuntu Linux.
# It uses Ansible to configure the target system.
#
# TODO:
#     - GUI applications are not working.
#     - add user and group
#     - workdir
#
# NOTE: Build docker image from project root:
#       "docker build -t development_on_ubuntu:latest -f docker/development_on_ubuntu/Dockerfile ."
#       Otherwise docker complains about the "COPY ansible /tmp/ansible" command.
#
#       Run docker container:
#       "docker run -ti --rm development_on_ubuntu:latest"
#

# Basic settings
FROM ubuntu:18.04

# Update the repository sources list
RUN apt-get update

# Copy ansible code to docker
RUN mkdir /tmp/ansible
COPY ansible /tmp/ansible

# Install ansible
RUN apt-get install -y python3-pip
RUN pip3 install -r /tmp/ansible/requirements.txt

# Run ansible playbook
RUN ansible-playbook /tmp/ansible/development_common.yml

# bash entrypoint
ENTRYPOINT /bin/bash
