FROM java:8-jre
MAINTAINER Jeremie Lesage <jeremie.lesage@gmail.com>

ENV JBAKE_VERSION=2.5.0 \
    JBAKE_SHA1=13f7a2b9fd064fcfe16a6862947364bb1c62d3d9 \
    JBAKE_DATA="/data"

RUN curl http://jbake.org/files/jbake-${JBAKE_VERSION}-bin.zip -o /root/jbake-bin.zip \
    && echo "$JBAKE_SHA1  /root/jbake-bin.zip" | sha1sum --status -c - \
    && unzip /root/jbake-bin.zip -d /opt \
    && rm /root/jbake-bin.zip

ENV JBAKE_HOME /opt/jbake-$JBAKE_VERSION/
ENV PATH $JBAKE_HOME/bin:$PATH

RUN mkdir -p "/data"
WORKDIR "$JBAKE_DATA"
RUN jbake -i

VOLUME "$JBAKE_DATA"
EXPOSE 8820

ENTRYPOINT ["jbake"]
CMD ["-b -s"]
