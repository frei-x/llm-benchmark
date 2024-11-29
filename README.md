大语言模型基准测试

python .\serving.py --dataset-name random  --random-input-len 1000 --random-output-len 100  --model Qwen/Qwen2-7B-Instruct --num-prompts 1 --trust-remote-code  --port 80   --base-url https://ai.gitee.com --endpoint /v1/chat/completions --api-key xxx --model-name Qwen2-7B-Instruct --backend openai-chat