# Video Compressor

A small desktop app that compresses videos to a target file size with FFmpeg, keeping quality as
high as the size budget allows. Handy for getting clips under upload limits (Discord, email, forms)
without doing the bitrate math by hand.

## Features

- Pick a target size in MB; the app derives the right bitrate from the video's duration
- Batch-compress a whole folder of videos at once
- H.264 (`libx264`) video with AAC audio
- Simple Tkinter GUI with a live progress view
- Works with a system FFmpeg or a custom FFmpeg path

## Requirements

- Python 3.9+
- [FFmpeg](https://ffmpeg.org/) and `ffprobe` on your PATH (or point the app at a custom path)
- `pip install tqdm`

## Usage

```bash
git clone https://github.com/halilibrahimyesirci/video-compressor
cd video-compressor
pip install tqdm
python video_compressor_gui.py
```

Choose an input file or folder, set the target size, and start — compressed files are written
alongside the originals.

## How it works

The app reads each video's duration with `ffprobe`, computes a video bitrate from your target size
(reserving ~128 kbps for audio), and re-encodes with `ffmpeg` using `libx264`. A smaller target
means a lower bitrate, so very aggressive targets trade away quality.

## License

[MIT](LICENSE)
