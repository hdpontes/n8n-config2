# Usa a imagem oficial do n8n (Alpine)
FROM n8nio/n8n:latest

USER root

# Instala pacotes adicionais no Alpine
RUN apk update && apk add --no-cache \
    wget \
    git \
    unzip \
    fontconfig \
    imagemagick \
    graphicsmagick \
    build-base \
    yasm \
    pkgconfig \
    libpng-dev \
    libjpeg-turbo-dev \
    libwebp-dev \
    libtiff-dev \
    ffmpeg \
    frei0r-plugins \
    rclone \
    && rm -rf /var/cache/apk/*

# Baixa e instala fontes Poppins
RUN mkdir -p /usr/share/fonts/poppins && \
    wget -q https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Regular.ttf -P /usr/share/fonts/poppins && \
    wget -q https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Bold.ttf -P /usr/share/fonts/poppins && \
    fc-cache -fv

# Volta para o usuário node
USER node

# Diretório de trabalho do n8n
WORKDIR /home/node/.n8n

# Porta padrão do n8n
EXPOSE 5678

CMD ["n8n"]
