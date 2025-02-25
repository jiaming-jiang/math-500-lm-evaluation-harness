### Model Performance Comparison

| Provider   | Model                  | Accuracy (%) |
|------------|------------------------|--------------|
| OpenAI     | o1-mini                | 90.0%        |
|            | o1-preview              | 85.5%        |
|            | o1                      | 94.8%        |
| DeepSeek   | R1                      | 97.3%        |
|            | V3                      | 90.2%        |
| Kimi       | k1.5 short              | 94.6%        |
|            | k1.5 long               | 96.2%        |
| Anthropic  | Claude 3.7 sonnet       | 82.2%        |
| Qwen       | QWQ-32B Preview         | 90.6%        |

### Install

To install the `lm-eval` package from the github repository, run:

```bash
git clone --depth 1 https://github.com/EleutherAI/lm-evaluation-harness
cd lm-evaluation-harness
pip install -e .
pip install -e ."[api]"
```

### User Guide

To evaluate a model using API on `math-500` you can use the following command :

```bash
set OPENAI_API_KEY=YOUR_API_KEY
python -m lm_eval \
    --model openai-chat-completions \
    --model_args model=gpt-4o,eos_string="</s>",max_length=2048,num_concurrent=5 \
    --apply_chat_template \
    --tasks math-500 \
    --num_fewshot 0 \
    --batch_size 1 \
    --log_samples \
    --output_path ../results/math500_gpt4o_results

```

### Results

You can find the evaluation results (sample output and logs) with gpt-4o in `results` folder.

## Cite as

```
@misc{eval-harness,
  author       = {Gao, Leo and Tow, Jonathan and Abbasi, Baber and Biderman, Stella and Black, Sid and DiPofi, Anthony and Foster, Charles and Golding, Laurence and Hsu, Jeffrey and Le Noac'h, Alain and Li, Haonan and McDonell, Kyle and Muennighoff, Niklas and Ociepa, Chris and Phang, Jason and Reynolds, Laria and Schoelkopf, Hailey and Skowron, Aviya and Sutawika, Lintang and Tang, Eric and Thite, Anish and Wang, Ben and Wang, Kevin and Zou, Andy},
  title        = {A framework for few-shot language model evaluation},
  month        = 07,
  year         = 2024,
  publisher    = {Zenodo},
  version      = {v0.4.3},
  doi          = {10.5281/zenodo.12608602},
  url          = {https://zenodo.org/records/12608602}
}
```
