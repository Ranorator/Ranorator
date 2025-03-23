FROM python:3.10-bookworm

RUN apt-get update && apt-get install -y \
    git \
    build-essential \
    pkg-config \
    ffmpeg \
    libavformat-dev \
    libavcodec-dev \
    libavdevice-dev \
    libavutil-dev \
    libavfilter-dev \
    libswscale-dev \
    libswresample-dev \
    && rm -rf /var/lib/apt/lists/*


WORKDIR /app

RUN git clone https://github.com/litagin02/Style-Bert-VITS2.git /app
RUN pip install --no-cache-dir "torch<2.4" "torchaudio<2.4" --index-url https://download.pytorch.org/whl/cu118
RUN pip install --no-cache-dir -r requirements.txt

RUN python initialize.py

CMD ["python", "server_fastapi.py"]