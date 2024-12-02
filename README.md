### 大语言模型性能、并发测试

#### 使用

pip install -r requirements.txt

#### 测试 glm-4-9b-chat /v1/completions

```
python serving.py --dataset-name random  --random-input-len 10 --random-output-len 200  --model THUDM/glm-4-9b-chat --num-prompts 1 --trust-remote-code  --port 80  --base-url https://ai.gitee.com  --api-key xxx --model-name glm-4-9b-chat --backend vllm
```

#### 测试 Qwen2.5-72B-Instruct /v1/chat/completions

额外添加参数，即可测试测试 chat/completions：
--backend openai-chat --endpoint /v1/chat/completions

```
 python serving.py --dataset-name random  --random-input-len 10 --random-output-len 100  --model Qwen/Qwen2.5-72B-Instruct --num-prompts 1 --trust-remote-code  --port 80   --base-url https://ai.gitee.com  --api-key xxx --model-name Qwen2.5-72B-Instruct --backend openai-chat --endpoint /v1/chat/completions
```

结果:
```
100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 1/1 [00:08<00:00,  8.22s/it]
Total input tokens:                      10
Total generated tokens:                  378
Request throughput (req/s):              0.12
Output token throughput (tok/s):         46.00
Total Token throughput (tok/s):          47.22
---------------Time to First Token----------------
Mean TTFT (ms):                          1346.34
Median TTFT (ms):                        1346.34
P99 TTFT (ms):                           1346.34
Mean ITL (ms):                           18.12
Median ITL (ms):                         17.98
P99 ITL (ms):                            33.91
==================================================
```

#### 参数说明
- --model 填写模型路径
需要下载模型 tokenizer 等配置文件，便于计算 tokens。
您可以添加环境变量 `HF_ENDPOINT=https://hf-api.gitee.com` python serving.py ...
或 model 填写本地模型路径

- --base-url api 提供商地址
- --api-key api 提供商的秘钥
- --model-name  请求体的 "model" 参数。api 提供商模型与 huggingface 模型路径不同时有用。
- --num-prompts  请求量
- --dataset-name random 使用随机数据，也可以添加数据集路径。
- --random-input-len 随机输入长度
- --random-output-len 随机输出长度，测试 chat/completions 时无法控制输出。
- --port 端口
- --endpoint， 默认为 /v1/completions