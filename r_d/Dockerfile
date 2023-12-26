FROM docker.io/nvidia/cuda:11.8.0-cudnn8-runtime-ubuntu22.04@sha256:85fb7ac694079fff1061a0140fd5b5a641997880e12112d92589c3bbb1e8b7ca

RUN apt-get update && apt-get install -y wget
RUN apt update
RUN apt-get install -y python3.10
RUN apt install -y git ffmpeg

WORKDIR /opt/roop

RUN git clone https://github.com/s0md3v/roop
WORKDIR /opt/roop/roop

RUN apt-get install -y python3-pip

COPY requirements.txt .
RUN pip3 install -r requirements.txt

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y python3-tk


RUN wget https://huggingface.co/ezioruan/inswapper_128.onnx/resolve/main/inswapper_128.onnx -O inswapper_128.onnx
RUN mkdir models
RUN pip uninstall onnxruntime onnxruntime-gpu & pip install onnxruntime-gpu==1.15.1