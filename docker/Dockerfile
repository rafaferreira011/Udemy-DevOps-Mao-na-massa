<<<<<<< HEAD
FROM openjdk:8-jdk-alpine
RUN addgroup -S notes && adduser -D notes -G notes
ENV MAVEN_VERSION 3.5.4
ENV MAVEN_HOME /usr/lib/mvn
ENV PATH $MAVEN_HOME/bin:$PATH
RUN wget http://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz && \
  tar -zxvf apache-maven-$MAVEN_VERSION-bin.tar.gz && \
  rm apache-maven-$MAVEN_VERSION-bin.tar.gz && \
  mv apache-maven-$MAVEN_VERSION /usr/lib/mvn
RUN apk --update add git
RUN mkdir /opt/note
RUN chown -R notes:notes /opt/note
USER notes:notes
WORKDIR /opt/note
RUN git clone https://github.com/callicoder/spring-boot-mysql-rest-api-tutorial.git /opt/note
RUN mvn package -Dmaven.test.skip=true
ARG JAR_FILE=*.jar
RUN cp ./target/easy-notes-1.0.0.jar /opt/notes/easy-note.jar
COPY application.properties application.properties
=======
FROM openjdk:8-jdk-alpine
RUN addgroup -S notes && adduser -D notes -G notes
USER notes:notes
ARG JAR_FILE=*.jar
COPY ${JAR_FILE} easy-note.jar
COPY application.properties application.properties
>>>>>>> a6a79c0cee6779046b9c518b3aabec63a0e17a02
ENTRYPOINT ["JAVA", "-jar", "easy-note.jar"]