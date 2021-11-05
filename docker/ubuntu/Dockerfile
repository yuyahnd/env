ARG UBUNTU_VERSION=20.04
FROM ubuntu:${UBUNTU_VERSION}

# Time zone Setting
RUN apt-get update && apt-get install -y tzdata
ARG TZ=UTC
ENV TZ ${TZ}

# Language Setting
ARG LANG=POSIX
RUN if [[ ${LANG} =~ ^jp_JP ]]; then \
    apt-get update && apt-get install -y language-pack-ja-base language-pack-ja locales \
    && locale-gen &{LANG} \
;fi
ENV LANG ${LANG}

# Install Library
RUN apt-get update && apt-get install -y \
    wget \
    curl \
    xz-utils \
    make \
    build-essential \
    libssl-dev \
    zlib1g-dev \
    libbz2-dev \
    libreadline-dev \
    libsqlite3-dev \
    llvm \
    libncurses5-dev \
    libncursesw5-dev \
    tk-dev \
    libffi-dev \
    liblzma-dev \
    libgdbm-dev \
    libdb-dev \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Install Python
WORKDIR /usr/local/src
RUN wget https://www.python.org/ftp/python/3.8.12/Python-3.8.12.tar.xz \
    && tar Jxf Python-3.8.12.tar.xz \
    && cd Python-3.8.12 \
    && ./configure \
    && make && make install \
    && pip3 install --upgrade pip \
    && pip3 install --upgrade setuptools

ARG USER_NAME=ubuntu
RUN useradd -m -s /bin/bash ${USER_NAME}
USER ${USER_NAME}
WORKDIR /home/${USER_NAME}

CMD ["/bin/bash"]
