# Skynet

Skynet is an API server for AI services wrapping several APIs and models.

## Running

Download GGUF llama model (e.g. https://huggingface.co/TheBloke/Llama-2-7b-Chat-GGUF) and point LLAMA_PATH to it

```bash
poetry install
poetry run uvicorn skynet.main:app
```

Visit
http://127.0.0.1:8000/latest/docs#/
http://127.0.0.1:8000/openai-api/docs#/

### Using GPU acceleration on an M1 Mac

Run this before starting Skynet:

```bash
export LLAMA_CPP_LIB=`pwd`/libllama-bin/libllama-m1.so
```

Make sure you use the right file name.

## Some benchmarks

Summary:

Model | Input size | Document chunk size | Time to summarize (M1 CPU) | Time to summarize (GPU) |
|---|---|---|---|---|
| [llama-2-7b-chat.Q4_K_M.gguf][1] | 16000 chars | 4000 chars | ~87 sec | ~44 sec |
| [llama-2-7b-chat.Q4_K_M.gguf][1] | 8000 chars | 4000 chars | ~51 sec | ~28 sec  |

[1]: https://huggingface.co/TheBloke/Llama-2-7b-Chat-GGUF/blob/main/llama-2-7b-chat.Q4_K_M.gguf
