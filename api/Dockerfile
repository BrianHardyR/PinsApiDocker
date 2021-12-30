FROM ubuntu

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Africa/Nairobi

RUN apt-get update
RUN apt-get install git -y

RUN apt-get install -y imagemagick && \
    apt-get clean;

RUN apt-get update && \
    apt-get install -y openjdk-8-jdk && \
    apt-get install -y ant && \
    apt-get clean;

RUN apt-get update && \
    apt-get install ca-certificates-java && \
    apt-get clean && \
    update-ca-certificates -f;

RUN apt-get update && \
    apt-get install -y ffmpeg && \
    apt-get clean;

ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64/
RUN export JAVA_HOME

RUN $RANDOM && \
    git clone https://brianhardyr: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@github.com/BrianHardyR/PinsApi.git;

WORKDIR /PinsApi/

RUN git checkout version2 && \
    git config --global user.email "elibrianga@gmail.com" && \
    git config --global user.name "BrianHardyR" && \
    $RANDOM && \
    git pull;

ENV APP_HOME = /PinsApi/

RUN chmod +x ./gradlew
RUN ./gradlew build -x test
RUN ./gradlew assemble

ENV ARTIFACT_PATH = /build/libs/api-0.0.1-SNAPSHOT.jar

WORKDIR /PinsApi/build/libs/

EXPOSE 8080
EXPOSE 8081
ENTRYPOINT exec java -jar api-0.0.1-SNAPSHOT.jar


