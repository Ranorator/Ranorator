FROM debian:bookworm-slim

RUN apt-get update && apt-get upgrade -y && apt-get install -y \
    libatk1.0-0 \
    libatk-bridge2.0-0 \
    libcups2 \
    libgtk-3-0 \
    libgbm1 \
    libasound2 \
    libxcomposite1 \
    libxdamage1 \
    libxfixes3 \
    libxrandr2 \
    libpango-1.0-0 \
    libcairo2 \
    libatspi2.0-0 \
    libnss3 \
    libnspr4 \
    unzip \
    xvfb \
    socat \
    procps \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY COEIROINK_LINUX*.zip /app/

RUN find . -name "COEIROINK_LINUX*.zip" -print0 | xargs -0 unzip -d /app/ && \
    find . -name "COEIROINK_LINUX*.zip" -print0 | xargs -0 rm && \
    mv /app/COEIROINK_LINUX* /app/COEIROINK_LINUX

CMD bash -c "xvfb-run --auto-servernum ./COEIROINK_LINUX/coeiroink-v2 --no-sandbox & sleep 5 && socat TCP-LISTEN:80,fork,reuseaddr,bind=0.0.0.0 TCP:127.0.0.1:50032"