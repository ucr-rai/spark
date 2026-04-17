# NVIDIA DGX Spark Setup

## Installing vLLM from pre-built wheels

```bash
pip install torch==2.11.0+cu130 torchvision==0.26.0+cu130 torchaudio==2.11.0+cu130 --index-url https://download.pytorch.org/whl/cu130
pip install flashinfer-python==0.6.7 flashinfer-cubin==0.6.7
pip install https://github.com/ucr-rai/spark/releases/download/2026-04-17-1948d0c/vllm-2026.4.17-cp313-cp313-linux_aarch64.whl
```

## Building vLLM from source

Install Build Dependencies:
```bash
pip install setuptools_scm pybind11 build ninja
pip install flashinfer-python==0.6.7 flashinfer-cubin==0.6.7
```

Go to the source code folder and build:
```bash
cd ~/vllm_src
CUDA_HOME=/usr/local/cuda \
TORCH_CUDA_ARCH_LIST="12.0 12.1+PTX" \
MAX_JOBS=16 \
pip install -e . --no-build-isolation
```

## Benchmarking

```bash
wget https://huggingface.co/datasets/anon8231489123/ShareGPT_Vicuna_unfiltered/resolve/main/ShareGPT_V3_unfiltered_cleaned_split.json

vllm bench throughput --model NousResearch/Hermes-3-Llama-3.1-8B --dataset-name sharegpt --dataset-path ShareGPT_V3_unfiltered_cleaned_split.json --num-prompts 100
```