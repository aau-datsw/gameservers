FROM ubuntu:18.04
RUN apt-get update -qq && apt-get install -y xz-utils && rm -rf /var/lib/apt/lists/*
WORKDIR /factorio
COPY ./factorio_headless_x64_0.17.69.tar.xz /tmp
RUN tar -xf /tmp/factorio_headless_x64_0.17.69.tar.xz -C /
RUN rm /tmp/factorio_headless_x64_0.17.69.tar.xz
run ls /factorio
RUN chmod +x /factorio/bin/x64/factorio
COPY ./config/* /factorio/data/

RUN ./bin/x64/factorio --create /data/factorio_save.zip --map-gen-settings ./data/map-gen-settings.json --map-settings ./data/map-settings.json

EXPOSE 34197

CMD ./bin/x64/factorio --start-server /data/factorio_save.zip --server-settings ./data/server-settings.json
