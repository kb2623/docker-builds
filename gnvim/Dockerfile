FROM debian:bullseye-slim

# Update and install base programs
RUN apt update \
 && apt install --no-install-recommends -y bash make git ca-certificates cargo neovim libgtk-3-dev fonts-firacode

# Copy repository
ADD gnvim /opt/gnvim
# Build neovim-gtk
RUN cd /opt/gnvim \
 && make NOWEBKIT2GTK=1 \
 && make install

ENTRYPOINT bash
