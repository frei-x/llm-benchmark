### 大语言模型性能、并发测试
```
python serving.py --dataset-name random  --random-input-len 10 --random-output-len 200  --model THUDM/glm-4-9b-chat --num-prompts 1 --trust-remote-code  --port 80  --base-url https://ai.gitee.com  --api-key xxx --model-name glm-4-9b-chat --backend vllm
```

- --model 填写模型路径，需要下载模型 tokenizer 等配置文件，
您可以添加环境变量 `HF_ENDPOINT=https://hf-api.gitee.com` python serving.py ...
或 model 填写本地模型路径

- --base-url api 地址

- --api-key 秘钥

- --model-name  请求体的 "model"

- --num-prompts  请求量

