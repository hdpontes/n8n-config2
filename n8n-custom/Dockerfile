# Use a imagem oficial do n8n como base
FROM n8nio/n8n:latest

# Instala FFmpeg e plugins frei0r para efeitos
USER root
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

# Cria diretório para fontes adicionais (opcional)
RUN mkdir -p /usr/local/share/fonts/poppins && \
    curl -sLo /usr/local/share/fonts/poppins/Poppins-Regular.ttf https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Regular.ttf && \
    curl -sLo /usr/local/share/fonts/poppins/Poppins-Bold.ttf https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Bold.ttf && \
    fc-cache -fv

# Volta para usuário n8n
USER node

# Diretório de trabalho (mesmo do volume)
WORKDIR /home/node/.n8n

# Comando padrão para iniciar o n8n
ENTRYPOINT ["n8n"]
CMD ["start"]
