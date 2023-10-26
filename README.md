# llamalog
All Credits to HuggingFace Transformers and Microsoft for all transformers/deepspeed files (run_....py).

This is a research project I'm working on: Parameter-Efficient finetuning Code Llama for a Verilog Code Assistant.

ds_config.json for DeepSpeed Configuration.
peft2_llama.yml for environment.
```
conda env create -f peft2_llama.yml
```
For a dataset in folder named <Dataset>, please use this command for finetuning:
```
CUDA_VISIBLE_DEVICES=<device indexss> WANDB_DISABLED=TRUE deepspeed --master_port=<port> run_clm.py
--model_name_or_path=<model_name> --save_steps=1000 --per_device_train_batch_size=1 --learning_rate 2e-5 --num_train_epochs 1 --output_dir=<output_dir>
--report_to none --dataset_name <Dataset> --tokenizer_name <tokenizer_name> --block_size 1024 --gradient_accumulation_steps 32
--do_train --do_eval --fp16 --overwrite_output_dir --deepspeed ds_config.json
```
