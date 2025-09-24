# Use a imagem oficial do Node.js como base
FROM node:20-bullseye

# Instala FFmpeg e ferramentas básicas
RUN apt-get update && apt-get install -y \
    ffmpeg \
    curl \
    fontconfig \
    && rm -rf /var/lib/apt/lists/*

# Instala fontes Poppins
RUN mkdir -p /usr/local/share/fonts/poppins \
    && curl -sLo /usr/local/share/fonts/poppins/Poppins-Regular.ttf https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Regular.ttf \
    && curl -sLo /usr/local/share/fonts/poppins/Poppins-Bold.ttf https://github.com/google/fonts/raw/main/ofl/poppins/Poppins-Bold.ttf \
    && fc-cache -fv

# Cria diretório de trabalho
WORKDIR /usr/src/app

# Copia package.json (caso queira instalar pacotes extras)
COPY package*.json ./

# Instala dependências npm (se houver)
RUN npm install || echo "Sem pacotes npm extras"

# Copia o restante do código (caso tenha)
COPY . .

# Exposição da porta do n8n
EXPOSE 5678

# Comando padrão
CMD ["n8n"]
