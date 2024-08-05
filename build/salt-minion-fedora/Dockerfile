FROM fedora:39
ARG salt_version
COPY yum.conf /etc/yum.conf
RUN dnf update -y 
RUN dnf install -y procps-ng
RUN dnf install -y wget curl supervisor \
    && wget -O /install_salt.sh https://bootstrap.saltproject.io/ \
    && chmod +x /install_salt.sh \
    && /install_salt.sh -d -X stable $salt_version

#RUN rpm --import https://repo.saltproject.io/salt/py3/fedora/38/x86_64/SALT-PROJECT-GPG-PUBKEY-2023.pub
#RUN curl -fsSL https://repo.saltproject.io/salt/py3/fedora/38/x86_64/minor/$salt_version.repo | tee /etc/yum.repos.d/salt.repo
#RUN dnf install -y salt-minion
COPY supervisord.conf /etc/supervisor/supervisord.conf
ENTRYPOINT [ "/usr/bin/supervisord" ]
CMD [ "-c", "/etc/supervisor/supervisord.conf" ]
