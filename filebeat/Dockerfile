FROM centos:7
WORKDIR /opt
RUN curl https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-5.2.1-linux-x86_64.tar.gz | tar zx 
WORKDIR /opt/filebeat-5.2.1-linux-x86_64
COPY ./example_log logfile.log
COPY ./filebeat.yml filebeat.yml
CMD ./filebeat -e -c filebeat.yml -d "publish"

