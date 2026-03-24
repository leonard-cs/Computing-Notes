# 🤗 Hugging Face Notes

## Table of Contents
- [Hub](#hub)
- [Transformers](#transformers)
    - [Chat Templates](#chat-templates)
    - [Generation features](#generation-features)
        - [Streaming](#streaming)
    - [Quantization](#quantization)
- [TRL](#trl-transformers-reinforcement-learning)
- [PEFT](#peft-parameter-efficient-fine-tuning)

## Hub
[Doc](https://huggingface.co/docs/huggingface_hub/index)

Upload model:
```python
from huggingface_hub import login, upload_folder

login()

# Push your model files
upload_folder(folder_path="../checkpoint_models", repo_id="leonard-milo/Qwen3.5-2B-SFT-AutoConv-InstagramChat-Smart", repo_type="model")
```
## Transformers
### Chat templates
[Doc](https://huggingface.co/docs/transformers/chat_templating?template=Mistral#chat-templates)
### Generation features
- [Doc](https://huggingface.co/docs/transformers/v5.3.0/en/generation_features#generation-features)
- [🗂️ Decoding methods](https://huggingface.co/docs/transformers/generation_strategies)

#### Streaming
[Doc](https://huggingface.co/docs/transformers/v5.3.0/en/internal/generation_utils#transformers.TextStreamer)
- `TextStreamer`, `TextIteratorStreamer`
```python
from transformers import AutoModelForCausalLM, AutoTokenizer, TextStreamer

tokenizer = AutoTokenizer.from_pretrained("openai-community/gpt2")
model = AutoModelForCausalLM.from_pretrained("openai-community/gpt2")
inputs = tokenizer(["The secret to baking a good cake is "], return_tensors="pt")
streamer = TextStreamer(tokenizer)

_ = model.generate(**inputs, streamer=streamer, max_new_tokens=20)
```

### Quantization
[Doc](https://huggingface.co/docs/transformers/en/main_classes/quantization#quantization)
#### `BitsAndBytesConfig`
```python
bnb_config = BitsAndBytesConfig(
    load_in_4bit = True, # 模型将以4位量化格式加载
    bnb_4bit_quant_type = "nf4", # 指定4位量化的类型为 nf4 
    bnb_4bit_compute_dtype = torch.float16, # 计算数据类型 
    bnb_4bit_use_double_quant = False, # 表示不使用双重量化
)

# 模型加载
model = AutoModelForCausalLM.from_pretrained(
    model_name,
    quantization_config = bnb_config,
    device_map = {"": 0} # 将模型加载到设备0（通常是第一个GPU）
)
```

## TRL (Transformers Reinforcement Learning)
[Doc](https://huggingface.co/docs/trl/index)

### SFT (Supervised Fine-Tuning)
[Doc](https://huggingface.co/docs/trl/sft_trainer)

## PEFT (Parameter-Efficient Fine-Tuning)
- [Doc](https://huggingface.co/docs/peft/index)
- [🗂️ PEFT integration with different TRL trainers](https://huggingface.co/docs/trl/peft_integration)
- [📂 LoRA/QLoRA notebook](https://github.com/huggingface/trl/blob/main/examples/notebooks/sft_trl_lora_qlora.ipynb)