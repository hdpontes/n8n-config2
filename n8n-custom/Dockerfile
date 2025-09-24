# Dockerfile para n8n customizado com FFmpeg e frei0r
FROM node:20-bullseye

# Informações do maintainer
LABEL maintainer="Herbert Danilo Pontes <seu-email@dominio.com>"

# Atualiza e instala dependências essenciais + FFmpeg + frei0r
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        wget \
        curl \
        ca-certificates \
        git \
        unzip \
        fontconfig \
        ffmpeg \
        frei0r-plugins \
    && rm -rf /var/lib/apt/lists/*

# Instala fontes Poppins
RUN mkdir -p /usr/local/share/fonts/poppins && \
    wget -q https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Regular.ttf -O /usr/local/share/fonts/poppins/Poppins-Regular.ttf && \
    wget -q https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Bold.ttf -O /usr/local/share/fonts/poppins/Poppins-Bold.ttf && \
    fc-cache -fv

# Define diretório de trabalho
WORKDIR /home/node/.n8n

# Copia apenas package.json e package-lock.json se houver customizações
# (opcional, pode remover se não tiver pacotes extras)
# COPY package*.json ./
# RUN npm install

# Define usuário para rodar o n8n
USER node

# Exposição da porta do n8n
EXPOSE 5678

# Comando padrão
ENTRYPOINT ["n8n"]
CMD ["start"]
