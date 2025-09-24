# Base Node.js Debian para apt-get
FROM node:20-bullseye

# Instala dependências do sistema e FFmpeg + frei0r
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

# Diretório padrão do n8n (volume será mapeado aqui)
WORKDIR /home/node/.n8n

# Mantém usuário node (mais seguro)
USER node

# Porta padrão do n8n
EXPOSE 5678

# Comando de inicialização do n8n
CMD ["n8n"]
