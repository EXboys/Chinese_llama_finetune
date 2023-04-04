# Chinese_llama_finetune
llama中文微调资料

使用的是alpaca_lora，将以上文件下载到alpaca_data_cleaned.json同目录下，使用一下的命令行进行微调

Training (finetune.py)
This file contains a straightforward application of PEFT to the LLaMA model, as well as some code related to prompt construction and tokenization. PRs adapting this code to support larger models are always welcome.

Example usage:

```
python finetune.py \
    --base_model 'decapoda-research/llama-7b-hf' \
    --data_path './alpaca_data_finetun' \
    --output_dir './lora-alpaca'
 ```
 
We can also tweak our hyperparameters:

```
python finetune.py \
    --base_model 'decapoda-research/llama-7b-hf' \
    --data_path './alpaca_data_finetun' \
    --output_dir './lora-alpaca' \
    --batch_size 128 \
    --micro_batch_size 4 \
    --num_epochs 3 \
    --learning_rate 1e-4 \
    --cutoff_len 512 \
    --val_set_size 2000 \
    --lora_r 8 \
    --lora_alpha 16 \
    --lora_dropout 0.05 \
    --lora_target_modules '[q_proj,v_proj]' \
    --train_on_inputs \
    --group_by_length
```
