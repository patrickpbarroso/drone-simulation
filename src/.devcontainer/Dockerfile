FROM ros:humble
ARG patrick=patrick
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Create the user
RUN groupadd --gid $USER_GID $patrick \
    && useradd --uid $USER_UID --gid $USER_GID -m $patrick \
    #
    # [Optional] Add sudo support. Omit if you don't need to install software after connecting.
    && apt-get update \
    && apt-get install -y sudo \
    && echo $patrick ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$patrick \
    && chmod 0440 /etc/sudoers.d/$patrick
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y python3-pip
ENV SHELL /bin/bash

# ********************************************************
# * Anything else you want to do like clean up goes here *
# ********************************************************

# [Optional] Set the default user. Omit if you want to keep the default as root.
USER $patrick
CMD ["/bin/bash"]