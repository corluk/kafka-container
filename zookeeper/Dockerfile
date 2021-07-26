FROM debian:latest 
RUN DEBIAN_FRONTEND=noninteractive apt-get update -y 
RUN DEBIAN_FRONTEND=noninteractive apt install curl -y 
RUN curl -Lo /tmp/java_11.deb \
    https://cdn.azul.com/zulu/bin/zulu11.50.19-ca-jdk11.0.12-linux_amd64.deb
RUN dpkg -i /tmp/java_11.deb; apt-get -yf install \ 
        && rm /tmp/java_11.deb

RUN DEBIAN_FRONTEND=noninteractive apt-get -y install jq 
RUN APACHE_MIRROR=$(curl "https://www.apache.org/dyn/closer.cgi?as_json=1"| jq --raw-output '.preferred') \
     && curl -o /opt/zookeeper.tgz "${APACHE_MIRROR}/zookeeper/zookeeper-3.7.0/apache-zookeeper-3.7.0-bin.tar.gz"
RUN cd /opt && tar xzf zookeeper.tgz && mv apache-zookeeper* zookeeper && rm zookeeper.tgz
CMD echo "hello zookeeper"