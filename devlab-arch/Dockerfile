FROM archlinux

RUN pacman -Syu --noconfirm &&\
    pacman -S --noconfirm sudo &&\
    pacman -Scc --noconfirm

RUN groupadd -g 1000 devlab &&\
    useradd -m -s /bin/bash -g devlab -u 1000 devlab &&\
    echo "devlab ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/devlab &&\
    chmod 600 /etc/sudoers.d/devlab