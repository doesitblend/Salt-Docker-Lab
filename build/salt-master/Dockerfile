FROM ubuntu:22.04
ENV DEBIAN_FRONTEND=noninteractive
ARG salt_version
RUN apt-get update
RUN apt-get install -y curl wget supervisor
# Run Salt installer to just add a Salt master, but not start it
RUN wget -O /install_salt.sh https://bootstrap.saltproject.io/ \
    && chmod +x /install_salt.sh \
    && /install_salt.sh -X -M stable $salt_version \
    && rm -fv /install_salt.sh
COPY supervisord.conf /etc/supervisor/supervisord.conf
ENTRYPOINT [ "/usr/bin/supervisord" ]
CMD [ "-c", "/etc/supervisor/supervisord.conf" ]

