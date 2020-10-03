FROM archlinux

RUN pacman -Syu --noconfirm &&\
    pacman -S --noconfirm sudo &&\
    pacman -Scc --noconfirm

ENV CONTAINER_USER="devlab"
ENV CONTAINER_GROUP="devlab"
ENV CONTAINER_UID=1000
ENV CONTAINER_GID=1000

RUN groupadd -g ${CONTAINER_GID} ${CONTAINER_GROUP} &&\
    useradd -m -s /bin/bash -g ${CONTAINER_GROUP} -u ${CONTAINER_UID} ${CONTAINER_USER} &&\
    echo "${CONTAINER_USER} ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/${CONTAINER_USER} &&\
    chmod 600 /etc/sudoers.d/${CONTAINER_USER}