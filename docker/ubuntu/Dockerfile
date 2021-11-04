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
