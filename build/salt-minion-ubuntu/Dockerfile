FROM ubuntu:22.04
ENV DEBIAN_FRONTEND=noninteractive
ARG salt_version=latest
RUN apt-get update
RUN apt-get install -y curl wget supervisor
RUN wget -O /install_salt.sh https://bootstrap.saltproject.io \
    && chmod +x /install_salt.sh \
    && /install_salt.sh -d -X stable $salt_version
#RUN curl -fsSL -o /etc/apt/keyrings/salt-archive-keyring-2023.gpg https://repo.saltproject.io/salt/py3/ubuntu/22.04/amd64/SALT-PROJECT-GPG-PUBKEY-2023.gpg
#RUN echo "deb [signed-by=/etc/apt/keyrings/salt-archive-keyring-2023.gpg arch=amd64] https://repo.saltproject.io/salt/py3/ubuntu/22.04/amd64/minor/$salt_version jammy main" | tee /etc/apt/sources.list.d/salt.list
COPY supervisord.conf /etc/supervisor/supervisord.conf
ENTRYPOINT [ "/usr/bin/supervisord" ]
CMD [ "-c", "/etc/supervisor/supervisord.conf" ]
