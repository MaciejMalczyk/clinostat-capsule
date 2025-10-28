FROM ubuntu:24.04
RUN apt update && apt install -y openssh-server xz-utils
RUN wget https://nodejs.org/dist/v20.17.0/node-v20.17.0-linux-x64.tar.xz
RUN mkdir -p /usr/local/lib/nodejs
RUN tar -xJvf node-v20.17.0-linux-x64.tar.xz -C /usr/local/lib/nodejs
ENV PATH=$PATH:/usr/local/lib/nodejs/node-v20.17.0-linux-x64/bin
RUN npm i -g http-server
RUN sed -i "s/#Port 22/Port 8022/" /etc/ssh/sshd_config
RUN mkdir /run/sshd
RUN useradd img
RUN yes img | passwd img
RUN mkdir -p /home/img/.ssh && chown -R img:img /home/img/.ssh
RUN mkdir /images && cd /images
ENTRYPOINT /usr/sbin/sshd -D & http-server /images
