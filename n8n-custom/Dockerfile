FROM node:20-bullseye

# Instala dependências do sistema
RUN apt-get update && apt-get install -y \
      ffmpeg \
      frei0r-plugins \
      wget \
      curl \
      ca-certificates \
      git \
      unzip \
      fontconfig \
    && rm -rf /var/lib/apt/lists/*

# Instala n8n globalmente
RUN npm install -g n8n

WORKDIR /home/node/.n8n
