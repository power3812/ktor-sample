FROM gradle:jdk8 as builder

COPY build.gradle.kts .
COPY gradle.properties .
COPY src ./src

RUN gradle installDist

FROM openjdk:8-jdk
EXPOSE 8000:8000

RUN mkdir /cmd
COPY --from=builder /home/gradle/build/install/gradle /cmd
WORKDIR /cmd/bin

CMD ["./gradle"]