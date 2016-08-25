FROM java:8-alpine
MAINTAINER Jeremie Lesage <jeremie.lesage@gmail.com>

ENV JBAKE_VERSION=2.4.0 \
    JBAKE_SHA1=e53633c6cd6ba714a8876cadc02fe41e7790c5db

RUN curl http://jbake.org/files/jbake-${JBAKE_VERSION}-bin.zip -o /root/jbake-bin.zip \
    && echo "$JBAKE_SHA1  /root/jbake-bin.zip" | sha1sum --status -c - \
    && unzip /root/jbake-bin.zip -d /opt \
    && rm /root/jbake-bin.zip

ENV JBAKE_HOME=/opt/jbake-$JBAKE_VERSION/ \
    PATH=$JBAKE_HOME/bin:$PATH

RUN mkdir -p "/data"
WORKDIR /data

RUN jbake -i

VOLUME "/data"
EXPOSE 8820

ENTRYPOINT ["jbake"]
CMD ["-b -s"]
