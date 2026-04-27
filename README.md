# audio-splitter and audio-joiner

# audio-splitter & audio-joiner

A pair of command-line tools for splitting audio files into equal-length segments and rejoining them in custom order.

## Features

- **audio-splitter**: Split audio files into equal-length segments (wav or flac)
- **audio-joiner**: Join segments back together with optional reordering (default, reverse, random sort)
- Processing performed using ffmpeg
- Output directory support
- Supports wav and flac formats

## Quick Start

### Split an audio file

```bash
./audio-splitter -t 0.5 -i song.wav -o segment
```

Creates `segment_001.wav`, `segment_002.wav`, etc., each 0.5 seconds long.

### Join segments back together

```bash
./audio-joiner -d . -p 'segment_*.wav' -o output.wav
```

Joins all matching segments in sorted order into `output.wav`.

### Reverse the segment order

```bash
./audio-joiner -d . -p 'segment_*.wav' -o reversed.wav -s reverse
```

### Randomize segment order

```bash
./audio-joiner -d . -p 'segment_*.wav' -o shuffled.wav -s random
```

## Tools

### audio-splitter

Split audio into equal-length segments.

**Usage**: `./audio-splitter -t <seconds> -i <input> -o <pattern> [options]`

**Required arguments**:

- `-t, --time`: Segment duration in seconds
- `-i, --input`: Input audio file path
- `-o, --output`: Output file pattern

**Optional arguments**:

- `-d, --directory`: Output directory (must exist, relative to current directory)\n
- `-f, --format`: Output format: wav or flac (default: wav)\n
- `-v, --verbose`: Print verbose output\n
- `-h, --help`: Show help message

See [README-audio-splitter.txt](README-audio-splitter.txt) for full documentation.

### audio-joiner

Join audio segments into a single file.

**Usage**: `./audio-joiner -d <dir> -p <pattern> -o <filename> [options]`

**Required arguments**:

- `-d, --directory`: Directory containing input segments
- `-p, --pattern`: Glob pattern for input files
- `-o, --output`: Output file name

**Optional arguments**:

- `-f, --format`: Output format (inferred from filename if not specified)
- `-s, --sort`: Sort order: default, reverse, or random (default: default)
- `-v, --verbose`: Print verbose output
- `-h, --help`: Show help message

See [README-audio-joiner.txt](README-audio-joiner.txt) for full documentation.

## Requirements

- Python 3
- ffmpeg (must be installed and in PATH)

## Installation

```bash
chmod +x audio-splitter audio-joiner
```

Then use `./audio-splitter` and `./audio-joiner` in your workflow.

## Workflow Example

```bash
# Split a 1-minute file into half-second chunks
./audio-splitter -t 0.5 -i original.flac -o chunk -f flac -d segments

# Edit/rearrange chunks manually in the segments directory

# Join them back in random order
./audio-joiner -d segments -p 'chunk_*.flac' -o experimental.flac -s random
```

## License

MIT
