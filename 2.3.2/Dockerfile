FROM java:8-jre
MAINTAINER Jeremie Lesage <jeremie.lesage@gmail.com>

ENV JBAKE_VERSION=2.3.2 \
    JBAKE_SHA1=8daa2603b0277ee92ba216cf1d7e2d706f489382 \
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
