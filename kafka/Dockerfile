FROM debian:latest 
RUN DEBIAN_FRONTEND=noninteractive apt-get update -y 
RUN DEBIAN_FRONTEND=noninteractive apt install curl -y 
RUN curl -Lo /tmp/java_11.deb \
    https://cdn.azul.com/zulu/bin/zulu11.50.19-ca-jdk11.0.12-linux_amd64.deb
RUN dpkg -i /tmp/java_11.deb; apt-get -yf install \ 
        && rm /tmp/java_11.deb
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install jq 
RUN APACHE_MIRROR=$(curl "https://www.apache.org/dyn/closer.cgi?as_json=1"| jq --raw-output '.preferred') \
     && curl -o /opt/kafka.tgz "${APACHE_MIRROR}/kafka/2.8.0/kafka_2.13-2.8.0.tgz"
RUN cd /opt && tar xzf kafka.tgz && mv kafka_* kafka && rm kafka.tgz

CMD echo "hello Kafka"