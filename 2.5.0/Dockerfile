FROM maven:latest
MAINTAINER Jeremie Lesage <jeremie.lesage@gmail.com>

ENV JBAKE_VERSION 2.5.0-SNAPSHOT
ENV JBAKE_DATA "/data"

RUN git clone https://github.com/jbake-org/jbake.git jbake.git \
    && cd jbake.git \
    && mvn package -Dmaven.test.skip=true \
    && unzip dist/jbake-$JBAKE_VERSION-bin.zip -d /opt \
    && cd .. \
    && rm -rf /jbake.git/ /root/.m2/

ENV JBAKE_HOME /opt/jbake-$JBAKE_VERSION/
ENV PATH $JBAKE_HOME/bin:$PATH

WORKDIR "$JBAKE_DATA"
VOLUME "$JBAKE_DATA"
EXPOSE 8820

ENTRYPOINT ["jbake"]
CMD ["-b -s"]
