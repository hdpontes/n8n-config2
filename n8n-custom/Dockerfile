# Base oficial do n8n
FROM n8nio/n8n:2

# Instala FFmpeg, curl e fontconfig, além das fontes Poppins
USER root
RUN apt-get update && apt-get install -y \
    ffmpeg \
    curl \
    fontconfig \
    && rm -rf /var/lib/apt/lists/* \
    && mkdir -p /usr/local/share/fonts/poppins \
    && curl -sLo /usr/local/share/fonts/poppins/Poppins-Regular.ttf https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Regular.ttf \
    && curl -sLo /usr/local/share/fonts/poppins/Poppins-Bold.ttf https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Bold.ttf \
    && fc-cache -fv

# Volta para usuário padrão do n8n
USER node
WORKDIR /home/node/.n8n
