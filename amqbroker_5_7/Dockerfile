FROM java:8-jre

ENV ACTIVEMQ_VERSION 5.7.0
ENV ACTIVEMQ apache-activemq-$ACTIVEMQ_VERSION
ENV ACTIVEMQ_TCP=61616 ACTIVEMQ_HTTP=8989 ACTIVEMQ_WS=61614

ENV ACTIVEMQ_HOME /opt/activemq

RUN \
    curl -O http://archive.apache.org/dist/activemq/apache-activemq/$ACTIVEMQ_VERSION/$ACTIVEMQ-bin.tar.gz && \
    mkdir -p /opt && \
    tar xf $ACTIVEMQ-bin.tar.gz -C /opt/ && \
    rm $ACTIVEMQ-bin.tar.gz && \
    ln -s /opt/$ACTIVEMQ $ACTIVEMQ_HOME && \
    useradd -r -M -d $ACTIVEMQ_HOME activemq && \
    chown activemq:activemq /opt/$ACTIVEMQ -R

USER activemq

COPY activemq.xml /opt/activemq/conf/activemq.xml

WORKDIR $ACTIVEMQ_HOME
EXPOSE $ACTIVEMQ_TCP $ACTIVEMQ_HTTP $ACTIVEMQ_WS

CMD ["/bin/bash", "-c", "bin/activemq console"]
