---
name: transcript-formatter
description: Format raw transcription segments into clean timestamped text, markdown with headers, or structured JSON. Use when the user wants to clean up a transcript, format transcript output, convert transcript to markdown, or add timestamps to text.
triggers:
  - format transcript
  - clean up transcript
  - transcript to markdown
  - add timestamps
  - format subtitles
  - pretty print transcript
---

# Transcript Formatter

Converts raw transcription segments into various clean output formats.

## When to Use

Use after transcription when the user wants a specific output format, or when reformatting existing transcripts for readability.

## How to Use

### Timestamped plain text

```python
from scripts.video_transcriber import transcriber, utils

formatted = transcriber.format_transcript(segments)
# Output: [00:00:15] First sentence here.
#         [00:00:32] Second sentence here.
```

### Save to file

```python
transcriber.save_transcript(segments, Path("output.txt"))
```

### Markdown with section headers (for course transcripts)

When formatting course transcripts, create markdown files with lesson metadata:

```python
from pathlib import Path

def format_as_markdown(lesson: dict, segments: list) -> str:
    lines = [
        f"# {lesson.get('title', 'Untitled')}",
        "",
        f"**Section:** {lesson.get('section_slug', '')}",
        f"**Duration:** {lesson.get('duration_seconds', 0) // 60}m",
        f"**Words:** {lesson.get('word_count', 0):,}",
        "",
        "---",
        "",
    ]
    for seg in segments:
        ts = utils.format_timestamp(seg["start"])
        lines.append(f"{ts} {seg['text']}")
    return "\n".join(lines)
```

### JSON format

Transcript JSON files contain an array of segment objects:
```json
[
  {"start": 0.0, "end": 5.2, "text": "Hello and welcome."},
  {"start": 5.2, "end": 12.8, "text": "Today we are going to..."}
]
```

## Utilities

- `utils.format_timestamp(seconds)` — Returns `[HH:MM:SS]` string
- `utils.slugify(text)` — Creates filesystem-safe filename
