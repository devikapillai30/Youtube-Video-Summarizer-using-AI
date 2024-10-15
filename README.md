# Youtube-Video-Summarizer-using-AI
![image](https://github.com/user-attachments/assets/bf220e7a-f293-4663-9310-f74390db0c73)

This project automates the process of summarizing YouTube videos using OpenAI's Whisper for audio transcription and ChatGPT for summarization. The tool efficiently extracts audio from videos, transcribes it, and generates concise summaries.

## Table of Contents
- [Features](#features)
- [Usage](#usage)
- [Example](#example)

## Features
- **Audio Extraction:** Downloads audio from YouTube videos as .mp3 files using `yt-dlp`.
- **Audio Transcription:** Converts audio to text using OpenAI's Whisper model.
- **Summarization:** Generates both short and long summaries of the transcriptions using ChatGPT.
- **Output Management:** Saves summaries, raw audio, and processed chunks in a neatly organized directory.

## Functions

- **`find_audio_files(path, extension=".mp3")`**: Recursively searches for audio files with a specified extension in a given directory.

- **`youtube_to_mp3(youtube_url: str, output_dir: str) -> str`**: Downloads audio from a YouTube video and saves it as an MP3 file in the specified output directory.

- **`chunk_audio(filename, segment_length: int, output_dir)`**: Splits a long audio file into shorter segments based on the specified length (in seconds), necessary for handling long audio files.

- **`transcribe_audio(audio_files: list, output_file=None, model="whisper-1")`**: Transcribes the audio files using OpenAI's Whisper model and optionally saves the transcripts to a text file.

- **`summarize(chunks: list[str], system_prompt: str, model="gpt-3.5-turbo", output_file=None)`**: Summarizes the transcriptions using ChatGPT, returning both short and long summaries.

- **`summarize_youtube_video(youtube_url, outputs_dir)`**: Orchestrates the entire process of downloading a YouTube video, chunking the audio, transcribing, and summarizing the content, returning both a long and short summary.


## Usage
To summarize a YouTube video, run the following command:
from your_module import youtube_to_mp3, transcribe_audio, summarize

Define the YouTube URL and output directory
youtube_url = "youtube_url"
output_dir = "outputs/"

Step 1: Download audio from YouTube
audio_file = youtube_to_mp3(youtube_url, output_dir)

Step 2: Transcribe the audio
transcripts = transcribe_audio([audio_file])

Step 3: Summarize the transcriptions
long_summary, short_summary = summarize(transcripts, system_prompt="Summarize the following text.")
