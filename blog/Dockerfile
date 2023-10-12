# Use the official Ubuntu image as the base image
FROM ubuntu:22.04

# Install openssh-server packages and configure it.
RUN apt-get update && \
    apt-get install -y openssh-server git hugo && \
    apt-get clean && \
    hugo new site myblog && \
    cd myblog && \
    git clone https://ghproxy.com/https://github.com/Aaron-Yu1/hugo-tranquilpeak-theme.git \
              themes/hugo-tranquilpeak-theme && \
    mkdir /var/run/sshd && \
    echo 'root:P@ssw0rd' | chpasswd
# Add SSH config file
ADD sshd_config /etc/ssh/sshd_config
ADD authorized_keys /root/.ssh/

WORKDIR /myblog/

# Expose the Nginx port
EXPOSE 443

# Start the nginx service
CMD ["hugo", "server", "--bind", "0.0.0.0","--port", "443", "--baseURL", "https://www.opscoffee.com", "--config", "themes/hugo-tranquilpeak-theme/exampleSite/config.toml", "--contentDir", "themes/hugo-tranquilpeak-theme/exampleSite/content"]
