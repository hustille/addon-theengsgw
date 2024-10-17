ARG BUILD_FROM
FROM ${BUILD_FROM}
LABEL io.hass.version="${BUILD_VERSION}" io.hass.type="addon" io.hass.arch="${BUILD_ARCH}"

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y build-essential bluez
RUN apt-get install -y python3 python3-pip python3-venv

# ENV VIRTUAL_ENV=/root/venv/theengs
# RUN python3 -m venv $VIRTUAL_ENV
# ENV PATH="$VIRTUAL_ENV/bin:$PATH"
ENV PIP_BREAK_SYSTEM_PACKAGES=1

RUN pip install --extra-index-url=https://www.piwheels.org/simple TheengsGateway==1.5.0

ENV current /root
ENV HOME $current
WORKDIR $current
COPY run.sh /root
COPY entrypoint.sh /root
RUN chmod a+x /root/run.sh
RUN chmod a+x /root/entrypoint.sh
ENTRYPOINT ["/root/entrypoint.sh"]
CMD [ "/root/run.sh" ]
