FROM bellsoft/liberica-openjdk-debian:8

USER root

RUN apt-get update && apt-get install -y unzip

RUN curl -L https://services.gradle.org/distributions/gradle-4.2.1-bin.zip --output gradle-4.2.1-bin.zip \
    && unzip gradle-4.2.1-bin.zip -d /opt \
    && rm gradle-4.2.1-bin.zip

ENV GRADLE_HOME /opt/gradle-4.2.1
ENV PATH $PATH:/opt/gradle-4.2.1/bin
ENV GRADLE_USER_HOME /home/gradle/.gradle

COPY gretl /usr/local/bin/
COPY __jars4image /home/gradle/libs/

COPY init.gradle /home/gradle/

RUN mkdir -p ~/.gradle && echo "org.gradle.daemon=false" >> ~/.gradle/gradle.properties \
    chown -R 1001:0 /home/gradle && \
    chmod -R g+rw /home/gradle && \
    ls -la /usr/local/bin/  && \
    ls -la /home/gradle && \
    ls -la /home/gradle/libs

USER 1001