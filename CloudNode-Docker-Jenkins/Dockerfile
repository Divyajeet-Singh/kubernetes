FROM ubuntu:16.04
RUN     apt-get update && \
         apt-get install -y openssh-server curl openjdk-8-jre git && \
         mkdir /var/run/sshd && \
         echo 'root:jenkins' | chpasswd && \
         sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
         sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd && \
         echo "export VISIBLE=now" >> /etc/profile && \
         curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && \
         chmod +x ./kubectl && \
         mv ./kubectl /usr/local/bin && \
         chown -hR root:root /root/ && \
         mkdir -p /jdk/bin/ && \
         ln /usr/bin/java /jdk/bin/java
COPY ./ca.crt  ./client.crt  ./client.key  ./config   /root/.kube/
ENV KUBECONFIG="/root/.kube/config"
ENV NOTVISIBLE "in users profile"
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
