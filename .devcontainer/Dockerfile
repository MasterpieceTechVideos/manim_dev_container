#FROM ubuntu:jammy
FROM nvidia/opengl:base-ubuntu22.04

# Add ubuntu user with same UID and GID as your host system, if it doesn't already exist
# Since Ubuntu 24.04, a non-root user is created by default with the name vscode and UID=1000
ARG USERNAME=ubuntu
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN if ! id -u $USER_UID >/dev/null 2>&1; then \
        groupadd --gid $USER_GID $USERNAME && \
        useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME; \
    fi
# Add sudo support for the non-root user
RUN apt-get update && \
    apt-get install -y sudo && \
    echo "$USERNAME ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/$USERNAME && \
    chmod 0440 /etc/sudoers.d/$USERNAME

# Switch from root to user
USER $USERNAME

# Add user to video group to allow access to webcam
RUN sudo usermod --append --groups video $USERNAME

# Update all packages
RUN sudo apt update && sudo apt upgrade -y

# Install Git
RUN sudo apt install -y \
    build-essential \
    ffmpeg \
    git \
    libcairo2-dev \ 
    libgl1-mesa-dev libgl1-mesa-glx \
    libpango1.0-dev \
    locales \
    mesa-utils \
    python3-dev python3-pip python3.10-venv \
    texlive \
    texlive-bibtex-extra \
    texlive-lang-english \
    texlive-luatex \
    texlive-metapost \
    texlive-science \
    wget 

# These require selection of geographic area that fits your language settings
# sudo apt-get install -y texlive-formats-extra texlive-fonts-extra 
# sudo apt-get install -y texlive-latex-extra texlive-xetex texlive-pictures 


# Create Python env for installation
WORKDIR /home/ubuntu
RUN python3 -m venv /home/ubuntu/venv
RUN echo "source ~/venv/bin/activate" >> ~/.bashrc

# Git clone and install Manim
RUN sudo wget \
    https://gist.githubusercontent.com/MasterpieceNKA/e90aff717a0f52c67c51a07f080542e5/raw/b2496a9ed60dcfbc9ef51a928d7f0fd84ffe88f3/manim_setup.sh \
    -P /tmp
RUN sudo chmod +x /tmp/manim_setup.sh
RUN /tmp/manim_setup.sh
