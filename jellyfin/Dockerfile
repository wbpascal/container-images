ARG JELLYFIN_VERSION=10.8.13

FROM jellyfin/jellyfin:${JELLYFIN_VERSION}

# Define the variables here, otherwise it will not be visible to the RUN command below
ARG JELLYFIN_FFMPEG_VERSION=6.0.1-1
ARG TARGETPLATFORM

# Upgrade the machine, remove the installed jellyfin-ffmpeg version, install the new version, and then clean up again
RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install lsb-release -y \
    && apt-get remove jellyfin-ffmpeg* -y \
    && curl -Lo ~/jellyfin-ffmpeg.deb https://github.com/jellyfin/jellyfin-ffmpeg/releases/download/v${JELLYFIN_FFMPEG_VERSION}/jellyfin-ffmpeg$(echo "${JELLYFIN_FFMPEG_VERSION}" | cut -d '.' -f 1)_${JELLYFIN_FFMPEG_VERSION}-$(lsb_release -c -s 2> /dev/null)_$(echo "${TARGETPLATFORM}" | cut -d '/' -f 2).deb \
    && apt-get install ~/jellyfin-ffmpeg.deb -y \
    && rm ~/jellyfin-ffmpeg.deb \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*
