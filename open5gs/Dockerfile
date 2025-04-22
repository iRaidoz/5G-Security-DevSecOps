FROM ubuntu:22.04
ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y \
    build-essential meson ninja-build git \
    flex bison libsctp-dev libgnutls28-dev \
    libgcrypt20-dev libssl-dev libyaml-dev \
    mongodb && rm -rf /var/lib/apt/lists/*

COPY source /open5gs
WORKDIR /open5gs

RUN meson build --prefix=/usr && \
    ninja -C build && ninja -C build install

# Copie de configs minimalistes (à créer plus tard)
COPY config /etc/open5gs

ENTRYPOINT ["/usr/bin/open5gs-upfd"]
