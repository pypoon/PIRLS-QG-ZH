# PIRLS Category-specific Question Generation for Reading Comprehension
This repository is open-sourcing the data and code used in the [*PIRLS category-specific question generation for reading comprehension*](https://hdl.handle.net/10062/107171).

## Data
|Dataset                 | Training set (fine-tuning)           | Test set |
| :-------------------- | :----------------------------------------------------: | :----------------------------------------------------------: |
| Source | Published Chinese storybooks | TSA <sup>[1]</sup>|
| Excel file name | training (fine-tuning) set <sup>[2]</sup> | test set with generated questions & answers |

[1] https://www.bca.hkeaa.edu.hk/web/TSA/en/SecPaperSchema.html

[2] Articles have been replaced with article IDs due to copyright restrictions. If you would like to access the article contents for academic use, please contact Dr. Chu, the last author of the paper (skwchu@hkmu.edu.hk).

The prompts used in the experiments are stored in QAG_prompt_zero.xlsx

## Large Language Model and Code
### GPT
**model:** gpt-4o

**code:** GPT_question_generation.ipynb

Please replace OPENAI_API_KEY with your OpenAI API key at the beginning of the script.
```python
client = OpenAI(
    os.environ.get("OPENAI_API_KEY")
)
```

### Llama
**model:** [llama-3-chinese-8b-instruct-v2](https://huggingface.co/hfl/llama-3-chinese-8b-instruct-v2)

**code:** LLama_question_generation.ipynb

You need to select 'zero' or 'few' in 'way' to decide whether to use zero-shot or few-shot prompting.
```python
process(article_data, prompt_path, way)
```


## Fine-tuning Source Code
We used the fine-tuning code from https://github.com/ymcui/Chinese-LLaMA-Alpaca-3. Except for the max_seq_length (=3303) and num_train_epochs (=1), all other hyperparameters are the same as in the [source code](https://github.com/ymcui/Chinese-LLaMA-Alpaca-3/blob/main/scripts/training/run_sft.sh).





## Citation
Please citat following paper if you use any resources.

***PIRLS Category-specific Question Generation for Reading Comprehension*** (https://hdl.handle.net/10062/107171)
(to be updated)
