FROM debian:stretch-slim AS build-env
MAINTAINER Takis Issaris <takis@issaris.com>
RUN apt-get update && apt-get install -y bzip2 gcc make wget && apt-get clean
WORKDIR /app
RUN wget -O archive.tar.bz2 https://github.com/samhocevar/zzuf/releases/download/v0.15/zzuf-0.15.tar.bz2 && \
  tar xf archive.tar.bz2 && \
  rm archive.tar.bz2 && \
  cd zzuf-* && \
  ./configure && \
  make && \
  make install && \
  cd - && \
  rm -rf zzuf-*

FROM debian:stretch-slim
COPY --from=build-env /usr/local/bin/zzuf /usr/local/bin/zzuf
