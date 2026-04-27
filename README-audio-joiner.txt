audio-joiner
============

Join audio segments back into a single file using ffmpeg.

USAGE
-----

  ./audio-joiner -d <dir> -p <pattern> -o <n> [options]

REQUIRED ARGUMENTS
------------------

  -d, --directory <dir>   Directory containing input segment files
  -p, --pattern <glob>    Glob pattern for input files (e.g., 'segment_*.flac')
  -o, --output <n>        Output file name (e.g., 'output.flac')

OPTIONAL ARGUMENTS
------------------

  -f, --format <fmt>      Output format (e.g., flac, wav, mp3; inferred from filename if not specified)
  -s, --sort <order>      Sort order: default, reverse, or random (default: default)
  -v, --verbose           Print verbose output
  -h, --help              Show help message and exit

EXAMPLES
--------

  Join flac segments in default (sorted) order:
  ./audio-joiner -d segments -p 'segment_*.flac' -o output.flac

  Join with verbose output:
  ./audio-joiner -d chunks -p 'chunk_*.flac' -o reassembled.flac -v

  Join segments in reverse order:
  ./audio-joiner -d segments -p 'segment_*.flac' -o reversed.flac -s reverse

  Join segments in random order:
  ./audio-joiner -d segments -p 'segment_*.flac' -o shuffled.flac -s random -v

  Join wav files as flac in reverse order:
  ./audio-joiner -d chunks -p 'chunk_*.wav' -o output.flac -f flac -s reverse -v

NOTES
-----

  - Input segments are read from the specified directory
  - Output file is written to the same directory as input segments
  - Files are joined in sorted order (ascending) by default
  - Use -s reverse to reverse the sort order (descending)
  - Use -s random to randomize the order
  - Glob pattern must be quoted if it contains wildcards
  - Supports any audio format ffmpeg handles (flac, wav, mp3, etc.)
  - Uses ffmpeg's concat demuxer with stream copy for fast, lossless joining
  - Output format is inferred from filename extension if -f not specified
  - Directory argument must exist and be local to current working directory

DEPENDENCIES
------------

  - Python 3
  - ffmpeg (must be installed and in PATH)

INSTALLATION
------------

  chmod +x audio-joiner
