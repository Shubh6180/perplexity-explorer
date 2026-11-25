# Perplexity Explorer

**Live Demo:** [https://perplexity-explorer-blue.vercel.app](https://perplexity-explorer-blue.vercel.app)

An interactive, single-file (`index.html`) web app for exploring language-model perplexity right in the browser using HTML, CSS, plain JavaScript, and [Transformers.js](https://huggingface.co/docs/transformers.js) (`Xenova/distilgpt2`, quantized `q8`).

## Features

- **Section 1 – Type a sentence**: Enter any text (defaults to `I love Python`) or pick from sample sentences (`I love Python`, `Python love I`, `The capital of France is Paris`). Lazily downloads `Xenova/distilgpt2` on first click and prepends token `50256` so the first token also receives a probability.
- **Section 2 – Probability of each token → perplexity**: Shows a token-by-token breakdown (`#`, `Token` with spaces marked as `␣`, `Probability P`, and `1/P`) plus the three calculation steps using log-space averaging (`exp(mean(−ln P))`) to prevent overflow.
- **Section 3 – What does the model predict next?**: Displays the top 8 next-token probabilities from the final position as horizontal bars, highlighting the `#1` prediction.
- **Section 4 – Try it by hand (Simulated, not from the model)**: Live editable token and probability rows with `+ Add token`, `Remove`, and three presets (`I love Python` → `2.32`, `All 1/8` → `8`, `One surprising word` → `3.42`). Works completely offline.

## Running Locally

Serve `index.html` over HTTP (recommended so ES modules and WebAssembly load cleanly) and open it in a browser:

```bash
python3 -m http.server 8765
```

Then visit `http://localhost:8765`.
