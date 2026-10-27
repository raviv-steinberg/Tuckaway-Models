# Tuckaway Models

Model files that [Tuckaway](https://github.com/raviv-steinberg/Tuckaway-Releases) downloads for search by meaning, only
when a user turns that feature on. The app checks each file's size and SHA-256 before it uses it. Nothing about the
user or their clips is ever sent; the search runs entirely on their PC.

Each model is one release, tagged by model and version. App releases are in
[Tuckaway-Releases](https://github.com/raviv-steinberg/Tuckaway-Releases).

## meaning-model-gte-1

| | |
|---|---|
| File | `gte-multilingual-base-int8u8-ir9.onnx` |
| Size | 340,318,797 bytes |
| SHA-256 | `986673ab57cf87b87b5dfb5305e1c8181d91cce350d91845afd9747f20af9529` |
| License | Apache License, Version 2.0 (see `LICENSE` in the release) |

### Credits

- **gte-multilingual-base** by [Alibaba-NLP](https://huggingface.co/Alibaba-NLP/gte-multilingual-base), under the
  Apache License, Version 2.0.
- **ONNX export** by [onnx-community](https://huggingface.co/onnx-community/gte-multilingual-base)
  (`onnx/model_quantized.onnx`, int8), under the same license.

### Changes

This file is a modified copy of the onnx-community export. Two changes were made, and nothing else:

1. Its int8 weights and their zero points were rewritten as uint8 (each value plus 128), which stands for exactly the
   same numbers, so the model gives the same results, without the overflow signed weights can hit on processors without
   VNNI instructions.
2. Its ONNX IR version was set from 10 to 9, so ONNX Runtime 1.19 can read it; the model uses nothing IR version 10
   added.

The release's `NOTICE` gives the details. The tokenizer (`sentencepiece.bpe.model`) is not hosted here; Tuckaway
downloads it from its original publisher.

## License

The model files are distributed under the Apache License, Version 2.0, as their original works are. Each release holds
the license text (`LICENSE`) and a `NOTICE` describing what was changed.
