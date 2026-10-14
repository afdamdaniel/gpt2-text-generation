# GPT-2 Text Generation

Text generation with the pretrained GPT-2 model. Built with Python, Hugging Face Transformers, and PyTorch.

The notebook takes a short prompt and generates two different continuations. It picks a GPU if one is available. Otherwise it runs on CPU.

## Project Overview

- Loads the pretrained `gpt2` model with the Hugging Face `pipeline`.
- Detects the best device (CUDA GPU or CPU) automatically.
- Sets the generation options in one `GenerationConfig` object.
- Generates two outputs from one prompt.
- Prints the prompt and each result in a clean format.

This project uses the pretrained model only. It does not train or fine-tune GPT-2.

## Tools Used

- Python
- Hugging Face Transformers
- PyTorch
- Jupyter Notebook

## Generation Settings

| Setting | Value | What it does |
|---|---|---|
| `max_new_tokens` | 50 | Limits the length of the new text |
| `num_return_sequences` | 2 | Returns two outputs per prompt |
| `do_sample` | True | Picks words by probability, not always the top one |
| `temperature` | 0.75 | Lower values give safer text |
| `top_k` | 50 | Chooses from the 50 most likely next words |
| `top_p` | 0.92 | Chooses from words that make up 92% of the probability |
| `repetition_penalty` | 1.2 | Reduces repeated phrases |

## Project Structure

```
gpt2-text-generation/
├── README.md
├── requirements.txt
├── notebooks/
│   └── gpt2_text_generation.ipynb
└── outputs/
    └── sample_generated_text.txt
```

## How to Run

1. Clone the repository.

   ```bash
   git clone https://github.com/<your-username>/gpt2-text-generation.git
   cd gpt2-text-generation
   ```

2. Install the libraries.

   ```bash
   pip install -r requirements.txt
   ```

3. Open the notebook and run all cells.

   ```bash
   jupyter notebook notebooks/gpt2_text_generation.ipynb
   ```

The first run downloads the GPT-2 model. This needs an internet connection.

## Code Overview

| Function | Purpose |
|---|---|
| `resolve_device()` | Checks for a CUDA GPU and falls back to CPU |
| `build_generator()` | Loads GPT-2 and sets the pad token |
| `build_generation_config()` | Sets the generation options |
| `generate()` | Runs the model on a prompt |
| `display_results()` | Prints the prompt and the outputs |

GPT-2 has no pad token by default. The code uses the end-of-text token as the pad token.

## Sample Output

**Prompt:** `In the future, artificial intelligence will`

**Generated text 1**

> In the future, artificial intelligence will be able to do things like create more accurate information about a person's physical location. In this case there would also be no need for doctors or medical staff and you could simply take your own time with it all instead of being forced into doing so by

**Generated text 2**

> In the future, artificial intelligence will be able to predict what's going on in your life and how you're feeling.
> "If we don't have any way of knowing about that now," says Dr Jangong from China Academy for Information Sciences (ACIS), "we can

The outputs change on every run because sampling is random.

## Limitations

- GPT-2 is a small, older model. The text can be off topic or false.
- The quote and the person in Generated text 2 are made up by the model.
- The output stops at 50 new tokens, so sentences can end in the middle.

## Possible Next Steps

- Try other prompts and compare the results.
- Compare different values of `temperature` and `top_p`.
- Try a larger model such as `gpt2-medium`.
- Add a seed so results can be repeated.
