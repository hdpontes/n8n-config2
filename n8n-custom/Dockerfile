# --- Base Node.js ---
FROM node:20-bullseye-slim

# --- Instala dependências do sistema ---
RUN apt-get update && apt-get install -y --no-install-recommends \
    ffmpeg \
    frei0r-plugins \
    imagemagick \
    fonts-dejavu \
    wget \
    build-essential \
    python3 \
    fontconfig \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# --- Instala n8n globalmente ---
RUN npm install -g n8n

# --- Instala a fonte Poppins ---
RUN mkdir -p /usr/local/share/fonts/poppins && \
    wget https://raw.githubusercontent.com/google/fonts/main/ofl/poppins/Poppins-Regular.ttf -P /usr/local/share/fonts/poppins && \
    wget https://raw.githubusercontent.com/google/fonts/main/ofl/poppins/Poppins-Bold.ttf -P /usr/local/share/fonts/poppins && \
    fc-cache -fv

# --- Remove ENTRYPOINT do FFmpeg, evita conflito com n8n ---
ENTRYPOINT []

# --- Definindo usuário não-root ---
USER node
WORKDIR /home/node

# --- Volume para persistência de dados do n8n ---
VOLUME ["/home/node/.n8n"]

# --- Comando padrão ---
CMD ["n8n"]
