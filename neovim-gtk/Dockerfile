FROM debian:bullseye

# Update and install base programs
RUN apt update \
 && apt install --no-install-recommends -y bash git ca-certificates make cargo neovim libgtk-3-dev fonts-firacode

# Clone repository
RUN git clone -b master https://github.com/daa84/neovim-gtk.git /opt/neovim-gtk
# Build neovim-gtk
RUN cd /opt/neovim-gtk \
 && cargo build --release \
 && make install

ENTRYPOINT bash
