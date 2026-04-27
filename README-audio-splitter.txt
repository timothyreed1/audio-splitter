audio-splitter
==============

Split audio files into equal-length segments using ffmpeg.

USAGE
-----

  ./audio-splitter -t <seconds> -i <input> -o <o> [options]

REQUIRED ARGUMENTS
------------------

  -t, --time <seconds>    Segment duration in seconds (e.g., 0.5)
  -i, --input <file>      Input audio file path
  -o, --output <pattern>  Output file pattern (e.g., 'segment' produces
                          segment_001.wav, segment_002.wav, etc.)

OPTIONAL ARGUMENTS
------------------

  -d, --directory <dir>   Directory for output files (must exist, relative to current directory)
  -f, --format <fmt>      Output format: wav or flac (default: wav)
  -v, --verbose           Print verbose output
  -h, --help              Show help message and exit

EXAMPLES
--------

  Split a 1-minute file into half-second chunks (default wav format):
  ./audio-splitter -t 0.5 -i song.wav -o chunk

  Split into flac segments:
  ./audio-splitter -t 0.5 -i song.wav -o chunk -f flac

  Split into subdirectory with verbose output:
  ./audio-splitter -t 0.5 -i song.wav -o chunk -d segments -f flac -v

  Split into 1-second segments:
  ./audio-splitter -t 1 -i song.wav -o segment -f wav

NOTES
-----

  - Output files are numbered: pattern_001, pattern_002, etc.
  - Supported formats: wav, flac
  - Directory argument must exist and be local to current working directory
  - Uses ffmpeg stream copy for fast, lossless processing

DEPENDENCIES
------------

  - Python 3
  - ffmpeg (must be installed and in PATH)

INSTALLATION
------------

  chmod +x audio-splitter
