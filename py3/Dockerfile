FROM nvidia/cuda:12.0.0-cudnn8-devel-ubuntu22.04
ARG DEBIAN_FRONTEND=noninteractive

# パッケージの追加とタイムゾーンの設定
# 必要に応じてインストールするパッケージを追加してください
RUN apt-get update \
    && apt-get install -y \
    && apt-get install -y tzdata \
    && ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get update && apt-get install -y python3.9 python3-pip \
    && apt-get update \
    && apt-get install -y git \
    && apt-get install -y sudo \
    && apt-get install -y curl \
    && apt-get install -y file \
    && apt-get install -y make \
    && apt-get install -y htop

ENV TZ=Asia/Tokyo

# JupyterLab関連のパッケージ（いくつかの拡張機能を含む）
# 必要に応じて、JupyterLabの拡張機能などを追加してください
RUN python3 -m pip install --upgrade pip \
    &&  pip install --no-cache-dir \
    black \
    jupyterlab \
    jupyterlab_code_formatter \
    jupyterlab-git \
    lckr-jupyterlab-variableinspector \
    jupyterlab_widgets \
    ipywidgets \
    import-ipynb

# 基本パッケージ
# Pythonでよく利用する基本的なパッケージです
# JupyterLabの動作には影響しないので、必要に応じてカスタマイズしてください
RUN pip install --no-cache-dir \
    numpy \
    pandas \
    scipy \
    scikit-learn \
    pycaret \
    matplotlib \
    japanize_matplotlib \
    tensorflow \
    torch \
    torchvision \
    keras \
    gensim \
    janome

# 追加パッケージ（必要に応じて）
# 各環境に特化したパッケージがある場合、この部分に追加します
RUN pip install --no-cache-dir \
    pydeps \
    graphviz \
    pandas_profiling \
    shap \
    umap \
    xgboost \
    lightgbm

# 研究室用追加パッケージ
RUN pip install --no-cache-dir \
    pip install praat-parselmouth