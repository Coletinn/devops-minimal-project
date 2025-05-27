FROM amazonlinux:2

# Install dependencies
RUN yum update -y && \
    yum install -y wget && \
    wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo && \
    rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key && \
    yum install -y java-17-amazon-corretto && \
    yum install -y jenkins

# Expose Jenkins port
EXPOSE 8080

# Start Jenkins
CMD ["/usr/bin/java", "-jar", "/usr/share/java/jenkins.war"]
