FROM "ubuntu:20.04"
RUN apt-get update

ARG USERNAME
ARG USER_UID
ARG USER_GID
ENV USERNAME=${USERNAME}

USER root

# Installing majority of packages
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
     && apt-get -y install --no-install-recommends \
     git \
     xdg-utils \
     locales \
     sudo \
     nano \
     vim \
     libtinfo5 \
     ca-certificates \
     tzdata \
     update-inetd \
     apt-utils \
     less \
     curl \
     wget \
     dpkg

RUN locale-gen en_US.UTF-8

ENV \
     LANG=en_US.UTF-8 \
     LC_ALL=en_US.UTF-8 \
          #some packages will require this to be set. You can change this a rebuild
          #the image is needed
     TZ="America/Detroit" \
     LANGUAGE=en_US.UTF-8

# Create the user
 RUN if getent passwd $USER_UID > /dev/null; then userdel -r $(getent passwd $USER_UID | cut -d ':' -f 1); fi \ 
    && groupadd --force --gid $USER_GID $USERNAME \
    && useradd --no-log-init --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && mkdir -p /etc/sudoers.d/ \
    # [Optional] Add sudo support. Omit if you don't need to install software after connecting.
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

USER $USERNAME

WORKDIR /home/${USERNAME}