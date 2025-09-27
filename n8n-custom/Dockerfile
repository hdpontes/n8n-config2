# --- Base n8n Alpine ---
FROM n8nio/n8n:latest

# Executar como root para instalar pacotes
USER root

# --- Pacotes do sistema (Alpine) ---
RUN apk add --no-cache \
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
    tiff-dev \
    ffmpeg \
    frei0r-plugins \
    rclone \
    bash \
    curl

# --- Instalar fontes Poppins ---
RUN mkdir -p /usr/local/share/fonts/poppins && \
    wget -q https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Regular.ttf -P /usr/local/share/fonts/poppins && \
    wget -q https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Bold.ttf -P /usr/local/share/fonts/poppins && \
    fc-cache -fv || true

# --- Configurações do contêiner ---
USER node
WORKDIR /home/node/.n8n
EXPOSE 5678

# Comando padrão para iniciar o n8n
CMD ["n8n"]
