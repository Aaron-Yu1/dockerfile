# Use the official Ubuntu image as the base image
FROM ubuntu:22.04

# Install openssh-server packages and configure it.
RUN apt-get update && \
    apt-get install -y git hugo && \
    apt-get clean && \
    hugo new site myblog && \
    cd myblog && \
    git clone https://ghproxy.com/https://github.com/Aaron-Yu1/hugo-tranquilpeak-theme.git \
              themes/hugo-tranquilpeak-theme && \
    rm -rf content && \
    mkdir {config,content}

WORKDIR /myblog/

# Expose the Nginx port
EXPOSE 443

# Start the nginx service
CMD ["hugo", "server", "--bind", "0.0.0.0","--port", "443", "--baseURL", "https://www.opscoffee.com", "--config", "content/config.toml"]
