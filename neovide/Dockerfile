FROM debian:bullseye-slim

# Update and install base programs
RUN apt update \
 && apt install -y bash curl gnupg ca-certificates git gcc-multilib g++-multilib cmake libssl-dev pkg-config libfreetype6-dev libasound2-dev libexpat1-dev libxcb-composite0-dev libbz2-dev libsndio-dev freeglut3-dev libxmu-dev libxi-dev

# Install vulkan SDK
RUN curl -sL "http://packages.lunarg.com/lunarg-signing-key-pub.asc" | apt-key add - \
 && curl -sLo "/etc/apt/sources.list.d/lunarg-vulkan-1.2.131-bionic.list" "http://packages.lunarg.com/vulkan/1.2.131/lunarg-vulkan-1.2.131-bionic.list" \
 && apt update \
 && apt install -y vulkan-sdk

# Install Rust
RUN cd /opt \
 && curl --proto '=https' --tlsv1.2 -sSf "https://sh.rustup.rs" -o rustup-init.sh \
 && sh rustup-init.sh -y

# Copy repository
ADD neovide /opt/neovide
# Build neovide
RUN cd /opt/neovide \
 && ~/.cargo/bin/cargo build --release \
 && cp ./target/release/neovide /usr/local/bin/neovide

ENTRYPOINT bash
