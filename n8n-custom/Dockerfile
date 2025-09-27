# Usa imagem oficial do n8n baseada em Debian
FROM n8nio/n8n:latest

USER root

# Instala pacotes adicionais
RUN apt-get update && apt-get install -y \
    wget \
    git \
    unzip \
    fontconfig \
    imagemagick \
    graphicsmagick \
    build-essential \
    libmagickwand-dev \
    libmagickcore-dev \
    yasm \
    pkg-config \
    libpng-dev \
    libjpeg-dev \
    libwebp-dev \
    libtiff-dev \
    libavcodec-extra \
    ffmpeg \
    frei0r-plugins \
    rclone \
    && rm -rf /var/lib/apt/lists/*

# Baixa e instala fontes Poppins
RUN mkdir -p /usr/local/share/fonts/poppins && \
    wget -q https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Regular.ttf -P /usr/local/share/fonts/poppins && \
    wget -q https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Bold.ttf -P /usr/local/share/fonts/poppins && \
    fc-cache -fv

# Volta para usuário padrão
USER node

# Diretório de trabalho do n8n
WORKDIR /home/node/.n8n

# Porta padrão
EXPOSE 5678

CMD ["n8n"]
