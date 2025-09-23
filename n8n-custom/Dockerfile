# Start from a standard, official Node.js image based on Alpine
FROM node:20-alpine

# Install OS-level dependencies for FFmpeg, Fonts, and Image Processing
RUN apk update && apk add --no-cache \
    ffmpeg \
    imagemagick \
    graphicsmagick \
    wget \
    fontconfig

# Install n8n globally using the Node Package Manager (npm)
RUN npm install -g n8n

# Install the Poppins font
RUN mkdir -p /usr/local/share/fonts/poppins && \
    wget https://raw.githubusercontent.com/google/fonts/main/ofl/poppins/Poppins-Regular.ttf -P /usr/local/share/fonts/poppins && \
    wget https://raw.githubusercontent.com/google/fonts/main/ofl/poppins/Poppins-Bold.ttf -P /usr/local/share/fonts/poppins && \
    fc-cache -fv

# The base Node image comes with a 'node' user. We'll use its home directory.
USER node
WORKDIR /home/node

# Standard command to start n8n
CMD ["n8n"]
