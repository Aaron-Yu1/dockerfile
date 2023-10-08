# Use the official Ubuntu image as the base image
FROM ubuntu:22.04

# Install openssh-server packages and configure it.
RUN apt-get update && \
    apt-get install -y openssh-server git hugo && \
    apt-get clean && \
    hugo new site myblog && \
    cd myblog && \
    git clone https://ghproxy.com/https://github.com/kakawait/hugo-tranquilpeak-theme.git \
              themes/hugo-tranquilpeak-theme && \
    mkdir /var/run/sshd && \
    echo 'root:P@ssw0rd' | chpasswd

# Add SSH config file
ADD sshd_config /etc/ssh/sshd_config
ADD authorized_keys /root/.ssh/

WORKDIR /myblog/themes/hugo-tranquilpeak-theme/exampleSite/

# Expose the SSH port
EXPOSE 1313

# Start the SSH server
CMD ["hugo", "server", "--themesDir", "../..", "--bind", "0.0.0.0", "--baseURL", "http://blog.test.local:1313"]
