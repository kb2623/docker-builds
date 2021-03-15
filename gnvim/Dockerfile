FROM debian:bullseye

# Update and install base programs
RUN apt update \
 && apt install --no-install-recommends -y bash make git ca-certificates cargo neovim libgtk-3-dev fonts-firacode

# Clone repository
RUN git clone -b master https://github.com/vhakulinen/gnvim.git /opt/gnvim
# Build neovim-gtk
RUN cd /opt/gnvim \
 && make NOWEBKIT2GTK=1 \
 && make install

ENTRYPOINT bash
