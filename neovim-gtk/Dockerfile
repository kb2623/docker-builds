FROM debian:bullseye

# Update and install base programs
RUN apt update \
 && apt install --no-install-recommends -y bash git ca-certificates make cargo neovim libgtk-3-dev fonts-firacode

# Copy repository
COPY neovim-gtk/ /opt/neovim-gtk/
# Build neovim-gtk
RUN cd /opt/neovim-gtk \
 && cargo build --release \
 && make install

ENTRYPOINT bash
