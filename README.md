# NVIDIA DGX Spark Setup

## Installing vLLM from pre-built wheels

pip install torch==2.11.0+cu130 torchvision==0.26.0+cu130 torchaudio==2.11.0+cu130 \
    --index-url https://download.pytorch.org/whl/cu130
pip install flashinfer-python==0.6.7 flashinfer-cubin==0.6.7
pip install https://github.com/ucr-rai/spark/releases/download/2026-04-17-1948d0c/vllm-2026.4.17+g1948d0c46.cu130-cp313-cp313-linux_aarch64.whl
