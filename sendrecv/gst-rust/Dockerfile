FROM maxmcd/gstreamer:1.14-buster

RUN wget -O rustup.sh https://sh.rustup.rs && sh ./rustup.sh -y
ENV PATH=$PATH:/root/.cargo/bin/

WORKDIR /opt/
COPY . /opt/
RUN cargo build

CMD echo "Waiting a few seconds for you to open the browser at localhost:8080" \
    && sleep 10 \
    && /opt/target/debug/webrtc-app --peer-id=1 --server=ws://signalling:8443
