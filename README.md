# EchoPrompt Reproducibiity Study
This README is a modified version of the original one in order to facilitate CS 421 course staff to run the code.
[Link to Paper](https://arxiv.org/abs/2309.10687)

### Clone the original paper repository and move into the echoprompt directory
```
git clone https://github.com/rajasekharmekala/echoprompt.git
<!-- alternatively is possible to run git clone https://github.com/DavideSalonico/echoprompt_rep_study.git to clone this repo which is just a fork with this updated README-->
cd echoprompt
```

### Install dependencies
```
<!-- Tested with python 3.9 -->
pip install -r requirements.txt
```

### Credentials
* create openai_key.txt file in root folder and add your openai api-key (sk-***). My personal api-key was removed for obvious reasons. It is necessary to purchase a [paid plan](https://platform.openai.com/docs/overview) in order to use APIs for this study, however I spent less than 10$ overall.

### Run an experiment
These are some of the experiment I ran for my reproducibility study. The particular experiment we are running in each line is self-explained by the name of the parameters.
```
<!-- on DROP_break dataset -->
## zero_shot
python main.py --model-name gpt-3.5-turbo --dataset drop_break --learning_mode zero_shot

## zero_shot+echoprompt
python main.py --model-name gpt-3.5-turbo --dataset drop_break --learning_mode zero_shot_cot --max_tokens 300 --zero_shot_prompt "Let's repeat the complete question. \"" --zero_shot_prompt_stage2 "Therefore, in arabic numerals, the answer is"

## standard
python main.py --model-name gpt-3.5-turbo --dataset drop_break --learning_mode standard --max_tokens 150
python main.py --model-name gpt-3.5-turbo --dataset drop_break --learning_mode standard_rephrase_v1 --max_tokens 300
python main.py --model-name gpt-3.5-turbo --dataset drop_break --learning_mode standard_rephrase_v2 --max_tokens 300
python main.py --model-name gpt-3.5-turbo --dataset drop_break --learning_mode standard_rephrase_v3 --max_tokens 300
python main.py --model-name gpt-3.5-turbo --dataset drop_break --learning_mode standard_qrepeat --max_tokens 300

## cot
python main.py --model-name gpt-3.5-turbo --dataset drop_break --learning_mode cot --max_tokens 450
python main.py --model-name gpt-3.5-turbo --dataset drop_break --learning_mode cot_rephrase_v1 --max_tokens 600
python main.py --model-name gpt-3.5-turbo --dataset drop_break --learning_mode cot_rephrase_v2 --max_tokens 600
python main.py --model-name gpt-3.5-turbo --dataset drop_break --learning_mode cot_rephrase_v3 --max_tokens 600
python main.py --model-name gpt-3.5-turbo --dataset drop_break --learning_mode cot_qrepeat --max_tokens 600

<!-- to run experiments on the multiarith dataset is enough to use the option --dataset multiarith and follow the previous examples -->
```

### Note
* Logs of the experiments can be found in the `logs` folder
* Final results of the experiments are saved in the `saved_results` folder
* The `max_tokens` parameter should be adjusted based on the task's complexity. More complex tasks, which necessitate longer explanations, will require a higher number of tokens. 

