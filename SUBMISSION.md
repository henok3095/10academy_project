# TRP 1 – AI Content Generation Challenge Submission

## 1. Environment Setup Documentation

- **APIs configured**
  - Google Gemini (for Lyria / Veo / Imagen): `GEMINI_API_KEY=<set locally in .env>`
  - AIMLAPI (for MiniMax with vocals): _not configured yet_ (optional for Part 1)
- **Steps performed**
  - Cloned repo earlier: `git clone https://github.com/10xac/trp1-ai-artist.git`
  - Entered project: `cd trp1-ai-artist`
  - Confirmed env file: `.env` already exists in the project root
  - Installed dependencies with uv:
    - `uv sync`
  - Verified CLI and configuration:
    - `uv run ai-content --help`
    - `uv run ai-content list-providers`
    - `uv run ai-content list-presets`
- **Issues encountered & resolutions**
  - So far, no installation or CLI issues: `uv sync` and the basic ai-content commands ran successfully.

---

## 2. Codebase Understanding

### 2.1 Architecture / Package Structure

- **Main modules under `src/ai_content/`:**
  - `core/` – protocols, registry, results, job tracking
  - `config/` – Pydantic settings and config loading
  - `providers/` – concrete integrations (Google, AIMLAPI/MiniMax, Kling, etc.)
  - `pipelines/` – orchestration for full content workflows (music, video, full)
  - `integrations/` – external services (Archive.org, media helpers, YouTube, etc.)
  - `presets/` – predefined music/video style presets
  - `utils/` – helpers (files, retries, lyrics parsing, etc.)
  - `cli/` – Typer-based command-line interface

### 2.2 Provider Capabilities

- **Music providers**
  - `lyria` (Google Gemini): instrumentals only, fast
  - `minimax` (AIMLAPI via AIMLAPI.com): supports vocals + reference audio, slower
- **Video providers**
  - `veo` (Google Gemini): text/video + image-to-video, fast prototyping
  - `kling` (KlingAI): higher quality, slower (not required for this challenge)
- **Vocals / lyrics support**
  - MiniMax via AIMLAPI is the provider that supports lyrics and vocals.

### 2.3 Preset System

- **Music presets** (from `music.py`):
  - `jazz` – 95 BPM – smooth jazz fusion
  - `blues` – 72 BPM – delta blues
  - `ethiopian-jazz` – 85 BPM – ethio-jazz fusion
  - `cinematic` – 100 BPM – epic orchestral
  - `electronic` – 128 BPM – progressive house
  - `ambient` – 60 BPM – atmospheric pads
  - `lofi` – 85 BPM – lo-fi hip-hop
  - `rnb` – 90 BPM – contemporary R&B
- **Video presets** (from `video.py`):
  - `nature` – wildlife documentary
  - `urban` – cyberpunk cityscape
  - `space` – astronaut / sci-fi
  - `abstract` – liquid metal / geometric
  - `ocean` – underwater scenes
  - `fantasy` – dragons / epic fantasy
  - `portrait` – fashion / beauty
- **How to add a new preset**
  - Add an entry to `presets/music.py` or `presets/video.py` with:
    - A unique name
    - Prompt / mood description
    - BPM (music) or aspect ratio / style details (video)

### 2.4 CLI Commands

- **Top-level**
  - `uv run ai-content --help`
  - `uv run ai-content list-providers`
  - `uv run ai-content list-presets`
- **Music command options**
  - `uv run ai-content music --style <preset> --provider <lyria|minimax> --duration <seconds>`
  - `uv run ai-content music --prompt "..." --provider lyria --bpm <int> --duration <seconds>`
  - `uv run ai-content music --prompt "..." --provider minimax --lyrics path/to/lyrics.txt`
- **Video command options**
  - `uv run ai-content video --style <preset> --provider veo --duration <seconds>`
  - `uv run ai-content video --prompt "..." --provider veo --aspect 16:9 --duration <seconds>`

_(You can refine this section with any extra flags you actually used.)_

---

## 3. Generation Log

### 3.1 Audio Generations (Instrumental)

- **Run 1 (Lyria, preset-based)**
  - Command:
    - `uv run ai-content music --style jazz --provider lyria --duration 30`
  - Prompt (implicit from preset): _smooth jazz fusion, walking bass_
  - Output file:
    - Path:
    - Duration:
    - File size:
  - Notes:

- **Run 2 (Lyria, custom prompt)**
  - Command:
    - `uv run ai-content music --prompt "..." --provider lyria --duration 30`
  - Prompt used:
  - Output file:
  - Notes:

### 3.2 Audio Generations (Vocals via MiniMax) – if configured

- **Run (MiniMax with lyrics)**
  - Lyrics file:
  - Command:
    - `uv run ai-content music --prompt "..." --provider minimax --lyrics path/to/lyrics.txt`
  - Output file:
  - Notes:

### 3.3 Video Generation

- **Run (Veo)**
  - Command:
    - `uv run ai-content video --style nature --provider veo --duration 5`
  - Style:
  - Output file:
  - Notes:

### 3.4 Bonus: Combined Music Video (FFmpeg)

- Command:
  - `ffmpeg -i video.mp4 -i music.wav -c:v copy -c:a aac -shortest output.mp4`
- Inputs:
  - Audio file:
  - Video file:
  - Final output:

_(Fill the paths / durations / notes from your actual runs.)_

---

## 4. Challenges & Solutions

- **Challenge 1**
  - Symptom:
  - Root cause:
  - Solution:
- **Challenge 2**
  - Symptom:
  - Root cause:
  - Solution:

_(Add as many as needed – API errors, timeouts, config issues, etc.)_

---

## 5. Insights & Learnings

- **What surprised you about the codebase**
  - e.g., the job tracker, preset design, multi-provider abstraction, etc.
- **What you would improve**
  - e.g., more explicit docs for providers, better error messages, presets for combined pipelines, etc.
- **Comparison to other AI tools you’ve used**
  - e.g., how this framework differs from direct calls to Gemini, OpenAI, etc.

---

## 6. Links

- **YouTube video(s)**
  - `[TRP1] Your Name – <Content Description>` – `<YOUTUBE_LINK_HERE>`
- **GitHub repo with artifacts**
  - `https://github.com/henok3095/10academy_project`
- **Any additional assets**
  - Local paths or cloud links to audio/video files (if applicable)

