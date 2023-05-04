FROM openjdk:17-alpine

LABEL org.opencontainers.image.source https://github.com/lmagomes/minecraft-containers

WORKDIR /app
RUN wget https://api.papermc.io/v2/projects/velocity/versions/3.2.0-SNAPSHOT/builds/252/downloads/velocity-3.2.0-SNAPSHOT-252.jar -O velocity.jar

WORKDIR /server
CMD cp /app/velocity.jar /server/velocity.jar && java -Xms512M -Xmx512M -XX:+UseG1GC -XX:G1HeapRegionSize=4M -XX:+UnlockExperimentalVMOptions -XX:+ParallelRefProcEnabled -XX:+AlwaysPreTouch -jar velocity.jar