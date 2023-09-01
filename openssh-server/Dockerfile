# Use the official Ubuntu image as the base image
FROM ubuntu:22.04

# Update the package list and install necessary packages
RUN apt-get update && \
    apt-get install -y openssh-server && \
    apt-get clean

# Configure the SSH server
RUN mkdir /var/run/sshd && \
    echo 'root:P@ssw0rd' | chpasswd && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# Expose the SSH port
EXPOSE 22

# Start the SSH server
CMD ["/usr/sbin/sshd", "-D"]
