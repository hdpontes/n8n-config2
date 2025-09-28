# Base n8n Alpine
FROM n8nio/n8n:stable

USER root

# Instalar pacotes essenciais + utilitários
RUN apk add --no-cache \
    wget \
    git \
    unzip \
    fontconfig \
    imagemagick \
    graphicsmagick \
    libpng-dev \
    libjpeg-turbo-dev \
    libwebp-dev \
    tiff-dev \
    frei0r-plugins \
    rclone \
    bash \
    curl \
    && rm -rf /var/cache/apk/*

# Baixar FFmpeg estático completo (pré-compilado) para evitar compilação pesada
# Baixa e extrai o FFmpeg static para /usr/local/bin
RUN wget -O /tmp/ffmpeg-release.tar.xz https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-amd64-static.tar.xz && \
    tar -xJf /tmp/ffmpeg-release.tar.xz -C /tmp && \
    cp /tmp/ffmpeg-*-static/ffmpeg /usr/local/bin/ && \
    cp /tmp/ffmpeg-*-static/ffprobe /usr/local/bin/ && \
    chmod +x /usr/local/bin/ffmpeg /usr/local/bin/ffprobe && \
    rm -rf /tmp/ffmpeg-release.tar.xz /tmp/ffmpeg-*-static

# Instalar fontes Poppins
RUN mkdir -p /usr/local/share/fonts/poppins && \
    wget -q https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Regular.ttf -P /usr/local/share/fonts/poppins && \
    wget -q https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Bold.ttf -P /usr/local/share/fonts/poppins && \
    fc-cache -fv || true

# Configurações finais
USER node

WORKDIR /home/node/.n8n

EXPOSE 5678

#CMD ["n8n"]
