Trials

python3.10 -m venv venv
source venv/bin/activate

pip install vllm
vllm serve PrimeIntellect/Qwen3-0.6B --gpu-memory-utilization 0.7 --max-model-len 4096

uv sync && uv sync --all-extras

export PYTORCH_CUDA_ALLOC_CONF=expandable_segments:True

uv run sft @ configs/debug/sft/train.toml