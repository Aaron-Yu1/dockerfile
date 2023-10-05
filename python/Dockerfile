# Use the official Ubuntu image as the base image
FROM ubuntu:22.04

# Install openssh-server packages and configure it.
RUN apt-get update && \
    apt-get install -y openssh-server pip openjdk-17-jdk git && \
    apt-get clean && \
    pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple && \
    pip install paramiko && \ 
    mkdir /share && \
    mkdir /var/run/sshd && \
    echo 'root:P@ssw0rd' | chpasswd

# Add SSH config file
ADD sshd_config /etc/ssh/sshd_config
ADD authorized_keys /root/.ssh/ 

# Expose the SSH port
EXPOSE 22

# Start the SSH server
CMD ["/usr/sbin/sshd", "-D"]
