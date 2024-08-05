FROM quay.io/centos/centos:stream9
ARG salt_version
COPY yum.conf /etc/yum.conf
RUN dnf install -y epel-release
RUN dnf upgrade -y \
    && dnf install --allowerasing -y curl wget supervisor vim-enhanced procps-ng
RUN wget --no-check-certificate -O /install_salt.sh https://bootstrap.saltproject.io/ \
    && chmod +x /install_salt.sh \
    && /install_salt.sh -X stable $salt_version \
    && rm -fv /install_salt.sh
ENTRYPOINT [ "/usr/bin/salt-minion" ]
CMD [ "-l", "info" ]

