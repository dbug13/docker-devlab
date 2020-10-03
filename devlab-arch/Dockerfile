FROM archlinux

RUN pacman -Syu --noconfirm &&\
    pacman -S --noconfirm sudo reflector &&\
    pacman -Scc --noconfirm

ENV CONTAINER_COUNTRY="United States"

RUN reflector --country "${CONTAINER_COUNTRY}" --latest 15 --sort rate --save /etc/pacman.d/mirrorlist

RUN groupadd -g 1000 devlab &&\
    useradd -m -s /bin/bash -g devlab -u 1000 devlab &&\
    echo "devlab ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/devlab &&\
    chmod 600 /etc/sudoers.d/devlab