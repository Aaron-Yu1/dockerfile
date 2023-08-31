From ubuntu:22.04

RUN apt update && \
    wget https://download.oracle.com/java/17/latest/jdk-17_linux-x64_bin.tar.gz -P /tmp && \
    mkdir /jenkins && \
    wget https://get.jenkins.io/war-stable/2.414.1/jenkins.war P /jenkins && \
    tar -zxf jdk-17_linux-x64_bin.tar.gz -C /usr/local/bin/ && \
    ln -s /usr/local/bin/jdk-17.0.6/ /usr/local/bin/jdk && \
    rm -rf jdk-17_linux-x64_bin.tar.gz

ENV JAVA_HOME=/usr/local/bin/jdk
ENV JRE_HOME=${JAVA_HOME}/jre
ENV CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
ENV PATH=$PATH:${JAVA_HOME}/bin/

EXPOSE 8080

CMD ["java", "-jar", "jenkins.war"]
