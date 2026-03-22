# 🤗 Hugging Face Notes

## Table of Contents
- [Hub](#hub)
- [Transformers](#transformers)
    - [Generation features](#generation-features)
        - [Streaming](#streaming)
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
[Doc](https://huggingface.co/docs/transformers/v5.3.0/en/generation_features#generation-features)

#### Streaming
[Doc](https://huggingface.co/docs/transformers/v5.3.0/en/internal/generation_utils#transformers.TextStreamer)
```python
from transformers import AutoModelForCausalLM, AutoTokenizer, TextStreamer

tokenizer = AutoTokenizer.from_pretrained("openai-community/gpt2")
model = AutoModelForCausalLM.from_pretrained("openai-community/gpt2")
inputs = tokenizer(["The secret to baking a good cake is "], return_tensors="pt")
streamer = TextStreamer(tokenizer)

_ = model.generate(**inputs, streamer=streamer, max_new_tokens=20)
```

## TRL (Transformers Reinforcement Learning)
[Doc](https://huggingface.co/docs/trl/index)

### SFT (Supervised Fine-Tuning)
[Doc](https://huggingface.co/docs/trl/sft_trainer)

## PEFT (Parameter-Efficient Fine-Tuning)
- [Doc](https://huggingface.co/docs/peft/index)
- [🗂️ PEFT integration with different TRL trainers](https://huggingface.co/docs/trl/peft_integration)