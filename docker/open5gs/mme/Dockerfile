FROM ubuntu:20.04

RUN apt update && apt install -y \
    git build-essential cmake libsctp-dev iproute2 iputils-ping net-tools \
    libyaml-dev libmongoc-dev libbson-dev meson ninja-build

RUN git clone https://github.com/open5gs/open5gs.git /open5gs && \
    cd /open5gs && \
    meson build --prefix=/usr && ninja -C build && ninja -C build install

COPY mme.yaml /etc/open5gs/mme.yaml

CMD ["open5gs-mmed", "-c", "/etc/open5gs/mme.yaml"]
