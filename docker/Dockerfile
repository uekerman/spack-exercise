FROM ubuntu:20.04

ENV DEBIAN_FRONTEND noninteractive

# Prohibit /usr/doc files from being installed
ADD 01_nodoc /etc/dpkg/dpkg.cfg.d/01_nodoc

# Fix timezone
RUN apt-get update && apt-get install -y apt-utils vim tmux htop git curl wget cmake build-essential sudo python3 python-is-python3 pkg-config python3-openssl bash gzip file openssl gnupg
# Tools for packaging
#RUN apt-get install -y libboost-all-dev
#RUN apt-get install -y libdeal.ii-dev

# Cleanup
RUN apt-get clean
#RUN rm -rf /var/lib/apt/lists/* && rm -rf /tmp/*
RUN rm -rf /tmp/*

# Create user
ARG USER_NAME=spackbuilder
ARG USER_HOME=/home/${USER_NAME}
#ARG USER_ID=1000
ARG USER_ID=1000
ARG GROUP_ID=1000

RUN groupadd -g $GROUP_ID "$USER_NAME"
RUN adduser \
    --home "$USER_HOME" \
    --uid $USER_ID \
    --gid $GROUP_ID \
    --disabled-password \
    "$USER_NAME"

RUN echo "$USER_NAME" ALL=\(root\) NOPASSWD:ALL > "/etc/sudoers.d/$USER_NAME" && \
    chmod 0440 "/etc/sudoers.d/$USER_NAME"

USER "$USER_NAME"
WORKDIR "$USER_HOME"

ENV USER "$USER_NAME"
ENV LD_LIBRARY_PATH /usr/local/lib:"${LD_LIBRARY_PATH}"
RUN git clone -b releases/v0.17 https://github.com/spack/spack.git spack && echo ". ${HOME}/spack/share/spack/setup-env.sh" >> ${USER_HOME}/.bashrc

CMD ["bash"]

# Reset frontend for interactive use
ENV DEBIAN_FRONTEND=
