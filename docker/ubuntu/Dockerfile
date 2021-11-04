ARG UBUNTU_VERSION=20.04
FROM ubuntu:${UBUNTU_VERSION}

# Time zone Setting
RUN apt-get update && apt-get install -y tzdata
ARG TZ=UTC
ENV TZ ${TZ}
