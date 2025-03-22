# Canary ASR API

A FastAPI-based REST API for NVIDIA's family of Canary-1B ASR (Automatic Speech Recognition) models.

## Features

- Fast and accurate speech-to-text transcription
- Real-time factor (RTF) calculation
- Processing time metrics
- Simple REST API interface

## Installation

1. Clone the repository:

```bash
git clone https://github.com/zetaphor/nemo-canary-fastapi.git
cd nemo-canary-fastapi
```

2. Install dependencies:

```bash
uv sync
```

3. Change the model in `api.py`:

Available models:

- [`nvidia/canary-1b`](https://huggingface.co/nvidia/canary-1b)
- [`nvidia/canary-1b-flash`](https://huggingface.co/nvidia/canary-1b-flash)
- [`nvidia/canary-180m-flash`](https://huggingface.co/nvidia/canary-180m-flash)

```python
canary_model = EncDecMultiTaskModel.from_pretrained('nvidia/canary-1b')
```

## Run the API:

```bash
python api.py
```

The server will start on `http://localhost:8000`

### Send transcription requests:

```bash
curl -X POST "http://localhost:8000/transcribe" \
    -H "Content-Type: application/json" \
    -d '{"audio_path": "/path/to/audio.wav"}'
```

### Example Response

```json
{
    "transcription": "Hello, world!",
    "processing_time_seconds": 0.12,
    "audio_duration_seconds": 1.0,
    "rtf": 0.12
}
```