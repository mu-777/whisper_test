# FROM python:3.9-slim
FROM pytorch/pytorch:2.0.0-cuda11.7-cudnn8-runtime
# FROM nvcr.io/nvidia/pytorch:22.09-py3

# タイムゾーン設定
ENV TZ=Asia/Tokyo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

WORKDIR /workspace

RUN apt update && apt install -y --no-install-recommends \
    sudo gosu less build-essential gcc git ffmpeg \
    && rm -rf /var/lib/apt/lists/*

# If pip is updated, installing whisper will fail with the error that "Cannot uninstall 'llvmlite'"
# RUN pip install --upgrade pip
RUN pip install git+https://github.com/openai/whisper.git@v20230314

RUN echo ALL ALL=\(ALL:ALL\) NOPASSWD: ALL>> /etc/sudoers

COPY ./entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
CMD ["bash"]