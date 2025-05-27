FROM amazonlinux:2

# Install dependencies
RUN yum update -y && \
    yum install -y \
        yum-utils \
        device-mapper-persistent-data \
        lvm2 \
        curl \
        wget \
        tar \
        openssh-server \
        passwd

# Install Docker
RUN amazon-linux-extras enable docker && \
    yum install -y docker && \
    yum clean all

# Create dockeradmin user
RUN useradd -m dockeradmin && \
    echo "dockeradmin:dockerpass" | chpasswd && \
    usermod -aG docker dockeradmin

RUN mkdir -p /opt/docker && \
    chown -R dockeradmin:dockeradmin /opt/docker

# SSH config
RUN mkdir /var/run/sshd && \
    sed -i 's/^#PermitRootLogin.*/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's/^#PasswordAuthentication.*/PasswordAuthentication yes/' /etc/ssh/sshd_config

# Gera as host keys para o SSH
RUN ssh-keygen -A

# Expose SSH
EXPOSE 22

# Script to start both dockerd and sshd
CMD /usr/sbin/sshd && dockerd

