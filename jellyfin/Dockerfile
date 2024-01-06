ARG JELLYFIN_VERSION=10.8.13

FROM jellyfin/jellyfin:${JELLYFIN_VERSION}

ARG JELLYFIN_FFMPEG_MAJOR_VERSION=6
ARG JELLYFIN_FFMPEG_VERSION=6.0.1-1

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get remove jellyfin-ffmpeg* -y \
    && curl -Lo ~/jellyfin-ffmpeg.deb https://github.com/jellyfin/jellyfin-ffmpeg/releases/download/v${JELLYFIN_FFMPEG_VERSION}/jellyfin-ffmpeg${JELLYFIN_FFMPEG_MAJOR_VERSION}_${JELLYFIN_FFMPEG_VERSION}-bullseye_amd64.deb \
    && apt-get install ~/jellyfin-ffmpeg.deb -y \
    && rm ~/jellyfin-ffmpeg.deb \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*
