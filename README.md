# llamalog
All Credits to HuggingFace and Microsoft for transformers/deepspeed files (run_....py) used in this repo.

Parameter-Efficient Finetuning Code Llama for a Verilog Code Assistant.

ds_config.json for DeepSpeed Configuration.
peft2_llama.yml for environment.
```
conda env create -f peft2_llama.yml
```
Put the fine-tuning dataset in a folder inside the directory. Please use this command for finetuning (replace <...> with parameters):
```
CUDA_VISIBLE_DEVICES=<device index(s)> WANDB_DISABLED=TRUE deepspeed --master_port=<port> run_clm.py
--model_name_or_path=<model_name> --save_steps=1000 --per_device_train_batch_size=1 --learning_rate 2e-5 --num_train_epochs 1 --output_dir=<output_dir>
--report_to none --dataset_name <Dataset> --tokenizer_name <tokenizer_name> --block_size 1024 --gradient_accumulation_steps 32
--do_train --do_eval --fp16 --overwrite_output_dir --deepspeed ds_config.json
```
