# Hugging Face Notes

Use this reference only when debugging or when the user asks how the skill works.

## Current integration assumptions

- Authentication uses a user-supplied Hugging Face API key.
- The API key should be a fine-grained token with Inference permission.
- **Default: uses HF Serverless Inference API (free daily ~4 min GPU quota), no provider specified.**
- Optional: user can specify `--provider` (e.g. `wavespeed`, `fal-ai`) to route to a paid third-party provider.
- Model is `Tongyi-MAI/Z-Image-Turbo`.
- The bundled script uses `huggingface_hub.InferenceClient(...).text_to_image(...)`.

## Defaults for this skill

- Provider: None (Serverless Inference API, free tier)
- Width: 1024
- Height: 1024
- Inference steps: 9
- Guidance scale: 0.0

## Common fixes

### Authentication or permission failure

Tell the user to verify:

1. The token is valid.
2. The token has permission to make calls to Inference Providers.
3. Their Hugging Face account has available usage or billing.

### Missing dependency

Run:

```bash
pip install -r scripts/requirements.txt
```
