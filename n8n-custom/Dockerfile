# --- Base image ---
FROM node:20-slim

# --- Variáveis de ambiente ---
ENV DEBIAN_FRONTEND=noninteractive

# --- Instala dependências do sistema + FFmpeg, frei0r e fontconfig ---
RUN apt-get update && apt-get install -y --no-install-recommends \
    ffmpeg \
    frei0r-plugins \
    imagemagick \
    fonts-dejavu \
    fontconfig \
    ca-certificates \
    wget \
    curl \
    python3 \
    build-essential \
    unzip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# --- Instala fontes Poppins localmente sem depender do GitHub ---
RUN mkdir -p /usr/local/share/fonts/poppins && \
    curl -sLo /usr/local/share/fonts/poppins/Poppins-Regular.ttf https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Regular.ttf && \
    curl -sLo /usr/local/share/fonts/poppins/Poppins-Bold.ttf https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Bold.ttf && \
    fc-cache -fv

# --- Diretório de trabalho ---
WORKDIR /usr/src/app

# --- Copia package.json e instala dependências npm ---
COPY package*.json ./
RUN npm install

# --- Copia código da aplicação ---
COPY . .

# --- Expõe porta padrão do n8n ---
EXPOSE 5678

# --- Comando de inicialização ---
CMD ["n8n"]
