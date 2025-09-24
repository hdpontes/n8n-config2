# Base Node.js Debian para apt-get
FROM node:20-bullseye

# --- Pacotes do sistema ---
RUN apt-get update && apt-get install -y \
    wget \
    curl \
    git \
    unzip \
    fontconfig \
    imagemagick \
    graphicsmagick \
    build-essential \
    yasm \
    pkg-config \
    libpng-dev \
    libjpeg-dev \
    libwebp-dev \
    libtiff-dev \
    libavcodec-extra \
    frei0r-plugins \
    ffmpeg \
    && rm -rf /var/lib/apt/lists/*

# Baixa e instala fontes Poppins
RUN mkdir -p /usr/local/share/fonts/poppins && \
    wget -q https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Regular.ttf -P /usr/local/share/fonts/poppins && \
    wget -q https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Bold.ttf -P /usr/local/share/fonts/poppins && \
    fc-cache -fv

# Instala n8n globalmente
RUN npm install -g n8n

# Diretório padrão do n8n (volume será mapeado aqui)
WORKDIR /home/node/.n8n

# Mantém usuário node (mais seguro)
USER node

# Porta padrão do n8n
EXPOSE 5678

# Comando de inicialização do n8n
CMD ["n8n"]
