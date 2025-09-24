# --- Base Image com FFmpeg full (Ubuntu) ---
FROM jrottenberg/ffmpeg:6.1-ubuntu

# --- Instala dependências do sistema ---
RUN apt-get update && apt-get install -y \
    curl \
    wget \
    fontconfig \
    unzip \
    git \
    python3 \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# --- Instala Node.js 20 ---
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs \
    && npm install -g npm

# --- Instala n8n globalmente ---
RUN npm install -g n8n

# --- Instala a fonte Poppins ---
RUN mkdir -p /usr/local/share/fonts/poppins \
    && wget https://raw.githubusercontent.com/google/fonts/main/ofl/poppins/Poppins-Regular.ttf -P /usr/local/share/fonts/poppins \
    && wget https://raw.githubusercontent.com/google/fonts/main/ofl/poppins/Poppins-Bold.ttf -P /usr/local/share/fonts/poppins \
    && fc-cache -fv

# --- Cria usuário 'node' e diretório de trabalho ---
RUN useradd -ms /bin/bash node
USER node
WORKDIR /home/node

# --- Persistência do n8n ---
VOLUME ["/home/node/.n8n"]

# --- Comando padrão para iniciar n8n ---
CMD ["n8n"]
