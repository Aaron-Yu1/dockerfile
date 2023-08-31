From ubuntu:22.04

RUN apt update && \
    apt install -y wget && \
    wget https://download.oracle.com/java/17/latest/jdk-17_linux-x64_bin.tar.gz -P /tmp && \
    mkdir /jenkins && \
    wget https://get.jenkins.io/war-stable/2.414.1/jenkins.war -P /jenkins && \
    tar -zxf /tmp/jdk-17_linux-x64_bin.tar.gz -C /usr/local/bin/ && \
    chown -R root:root /usr/local/bin/jdk-17.0.8 && \
    ln -s /usr/local/bin/jdk-17.0.8/ /usr/local/bin/jdk && \
    rm -rf /tmp/jdk-17_linux-x64_bin.tar.gz && \
    apt install -y libfreetype6 fontconfig

ENV JAVA_HOME=/usr/local/bin/jdk
ENV JRE_HOME=${JAVA_HOME}/jre
ENV CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
ENV PATH=$PATH:${JAVA_HOME}/bin/

EXPOSE 8080

CMD ["java", "-jar", "/jenkins/jenkins.war"]
