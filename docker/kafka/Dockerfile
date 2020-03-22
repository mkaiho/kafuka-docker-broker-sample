FROM openjdk:11 as builder

ENV KAFKA_LINK https://downloads.apache.org/kafka/2.4.1/kafka_2.12-2.4.1.tgz

WORKDIR /home/work

RUN mkdir kafka && curl ${KAFKA_LINK} | tar zx -C ./kafka --strip-components 1

FROM openjdk:11-jre-slim

WORKDIR /home/kafka

COPY --from=builder /home/work/kafka .
COPY start-kafka.sh /home/kafka/bin/start-kafka.sh

CMD ["bin/start-kafka.sh"]