# Usa a tag oficial para a versão mais recente em Alpine
FROM n8nio/n8n:latest-alpine

USER root

# Instala as dependências necessárias
RUN apk update && apk add --no-cache \
    ffmpeg \
    imagemagick \
    wget \
    fontconfig

# Instala a fonte Poppins
RUN mkdir -p /usr/local/share/fonts/poppins && \
    wget https://raw.githubusercontent.com/google/fonts/main/ofl/poppins/Poppins-Regular.ttf -P /usr/local/share/fonts/poppins && \
    wget https://raw.githubusercontent.com/google/fonts/main/ofl/poppins/Poppins-Bold.ttf -P /usr/local/share/fonts/poppins && \
    fc-cache -fv

USER node

# Comando padrão da imagem
CMD ["n8n"]
