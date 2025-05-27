FROM amazonlinux:2

# Install dependencies
RUN yum update -y && \
    yum install -y java-1.8.0-openjdk-devel wget tar

# Set environment variables
ENV CATALINA_HOME /opt/tomcat
ENV PATH $CATALINA_HOME/bin:$PATH

# Download and extract Tomcat
RUN wget https://downloads.apache.org/tomcat/tomcat-9/v9.0.105/bin/apache-tomcat-9.0.105.tar.gz && \
    mkdir -p /opt && \
    tar -xvzf apache-tomcat-9.0.105.tar.gz -C /opt && \
    mv /opt/apache-tomcat-9.0.105 /opt/tomcat && \
    rm apache-tomcat-9.0.105.tar.gz

# Expose port
EXPOSE 8080

# Start Tomcat
CMD ["/opt/tomcat/bin/catalina.sh", "run"]
