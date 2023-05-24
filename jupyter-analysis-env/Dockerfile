FROM python:3.10-buster

COPY requirements.txt ./

ARG DEBIAN_FRONTEND=noninteractive

# パッケージ追加とタイムゾーン設定
RUN apt-get update && apt-get install -y \
    tzdata git && \
    ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ENV TZ=Asia/Tokyo
ENV PATH="$HOME/.local/bin:$PATH"

# パッケージ追加（いくつかの拡張機能を含む）
# 1.JupyterLab関連
# 2.Pythonでよく利用する基本的なパッケージ
# 3.プロジェクトの特性に依存するパッケージ
RUN python3 -m pip install --upgrade pip && \
    pip install -r requirements.txt
