FROM debian:bullseye-slim

ENV PATH /usr/local/bin:$PATH

# Update and install base programs
RUN apt update \
 && apt install --no-install-recommends -y bash git ca-certificates make cmake cargo fonts-firacode pkg-config libfreetype6-dev libfontconfig1-dev libxcb-xfixes0-dev python3

# Clone repository
ADD alacritty /opt/alacritty
# Build alacritty
RUN cd /opt/alacritty \
 && cargo build --release \
 && cp target/release/alacritty /usr/local/bin/alacritty

ENTRYPOINT bash
