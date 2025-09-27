Trials

python3.10 -m venv venv
source venv/bin/activate

pip install vllm
vllm serve PrimeIntellect/Qwen3-0.6B --gpu-memory-utilization 0.7 --max-model-len 4096

uv sync && uv sync --all-extras

export PYTORCH_CUDA_ALLOC_CONF=expandable_segments:True

uv run sft @ configs/debug/sft/train.toml

uv run trainer @ configs/debug/rl/train.toml

uv run inference @ configs/debug/infer.toml



--


facebook/opt-125m

LiquidAI/LFM2-350M

facebook/MobileLLM-R1-140M  - does not support - flash-attn

HuggingFaceTB/SmolLM-135M
