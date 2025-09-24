# --- Base oficial do n8n ---
FROM n8nio/n8n:latest

# --- Instala ferramentas essenciais ---
USER root
RUN apt-get update && apt-get install -y \
    wget \
    curl \
    ca-certificates \
    git \
    unzip \
    fontconfig \
    && rm -rf /var/lib/apt/lists/*

# --- Instala FFmpeg full static build (todos codecs e filtros) ---
RUN mkdir -p /usr/local/bin/ffmpeg && \
    wget -O /tmp/ffmpeg-release-amd64-static.tar.xz https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-amd64-static.tar.xz && \
    tar -xvf /tmp/ffmpeg-release-amd64-static.tar.xz -C /tmp && \
    mv /tmp/ffmpeg-*-amd64-static/ffmpeg /usr/local/bin/ffmpeg && \
    mv /tmp/ffmpeg-*-amd64-static/ffprobe /usr/local/bin/ffprobe && \
    chmod +x /usr/local/bin/ffmpeg /usr/local/bin/ffprobe && \
    rm -rf /tmp/*

# --- Instala fontes Poppins (opcional, para textos em vídeos) ---
RUN mkdir -p /usr/local/share/fonts/poppins && \
    curl -sLo /usr/local/share/fonts/poppins/Poppins-Regular.ttf https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Regular.ttf && \
    curl -sLo /usr/local/share/fonts/poppins/Poppins-Bold.ttf https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Bold.ttf && \
    fc-cache -fv

# --- Configura diretório de trabalho ---
WORKDIR /home/node/.n8n

# --- Permite rodar como usuário padrão do n8n ---
USER node

# --- Verifica instalação do FFmpeg ---
RUN ffmpeg -version
