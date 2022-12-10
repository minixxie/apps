FROM eclipse-temurin:17.0.5_8-jdk-ubi9-minimal as jdk

RUN cd /usr/local \
	&& wget https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz \
	&& tar xzf apache-maven-3.8.6-bin.tar.gz \
	&& ln -sf /usr/local/apache-maven-3.8.6/bin/mvn /usr/local/bin/mvn \
	&& rm -rf /usr/local/apache-maven-3.8.6-bin.tar.gz

ARG APP_NAME

WORKDIR /app

ADD pom.xml .
RUN mvn dependency:go-offline

ADD . .
RUN mvn package -Dmaven.test.skip=true --offline
#RUN mvn package -Dmaven.test.skip=true

FROM eclipse-temurin:17.0.5_8-jre-ubi9-minimal

ARG APP_NAME
ENV APP_NAME=${APP_NAME}

#COPY --from=jdk 
