# labs-ai-models

The AI model used by the **AI code helper** on [lucavirtuoso.com](https://lucavirtuoso.com) (Sentience Labs).
It runs entirely in each visitor's browser, on their own CPU and GPU. These files are only stored here so
browsers can download them for free.

## What's here

`qwen2.5-coder-1.5b-instruct-q4_k_m.gguf`, split into 48 MB pieces in `parts/` (GitHub doesn't allow
files over 100 MB). `manifest.json` lists the pieces in order, with the size and SHA-256 of the whole
file. The browser downloads the pieces, joins them back together, checks the size and the hash, and loads
the model with [wllama](https://github.com/ngxson/wllama) (llama.cpp in WebAssembly).

To rebuild the original file yourself:

```
cat parts/qwen2.5-coder-1.5b-instruct-q4_k_m.gguf.part-* > qwen2.5-coder-1.5b-instruct-q4_k_m.gguf
sha256sum qwen2.5-coder-1.5b-instruct-q4_k_m.gguf   # must match manifest.json
```

## Credit and license

The model is **Qwen2.5-Coder-1.5B-Instruct** by the Qwen team (Alibaba Cloud), from
[Qwen/Qwen2.5-Coder-1.5B-Instruct-GGUF](https://huggingface.co/Qwen/Qwen2.5-Coder-1.5B-Instruct-GGUF),
unmodified apart from being split into pieces. It is licensed under the
[Apache License 2.0](LICENSE) (copied from the original repository).
