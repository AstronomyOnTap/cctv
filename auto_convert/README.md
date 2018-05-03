Packages to try and automatically transcribe video

First use ffmpeg to extract just the audio stream from a video

```bash
ffmpeg -i Evan.mp4 -acodec pcm16e Evan.wav
```

You should be able to output this as a .wav file (this is easiest to read in
python - aifc module can't read some of the aiff compressed files). If not, you
can convert aifc to wav files also using ffmpeg.

```bash
aot) gnarayan@grimnir|~/work/AoT_AV/cctv/auto_convert> ffmpeg -i Evan.aifc Evan.wav
ffmpeg version 3.4 Copyright (c) 2000-2017 the FFmpeg developers
  built with clang version 4.0.1 (tags/RELEASE_401/final)
  configuration: --prefix=/Users/gnarayan/anaconda3/envs/aot --disable-doc --enable-shared --extra-cflags='-fPIC -I/Users/gnarayan/anaconda3/envs/aot/include' --extra-cxxflags='=-fPIC' --extra-libs='-L/Users/gnarayan/anaconda3/envs/aot/lib -lz' --enable-pic --disable-static --disable-gpl --disable-nonfree --disable-openssl --enable-libvpx --cc=x86_64-apple-darwin13.4.0-clang --cxx=x86_64-apple-darwin13.4.0-clang++ --enable-libopus
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
Input #0, aiff, from 'Evan.aifc':
  Duration: 00:38:34.72, start: 0.000000, bitrate: 768 kb/s
    Stream #0:0: Audio: pcm_s16be (twos / 0x736F7774), 48000 Hz, mono, s16, 768 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (pcm_s16be (native) -> pcm_s16le (native))
Press [q] to stop, [?] for help
Output #0, wav, to 'Evan.wav':
  Metadata:
    ISFT            : Lavf57.83.100
    Stream #0:0: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 48000 Hz, mono, s16, 768 kb/s
    Metadata:
      encoder         : Lavc57.107.100 pcm_s16le
size=  217005kB time=00:38:34.72 bitrate= 768.0kbits/s speed=2.79e+03x
video:0kB audio:217005kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.000035%
```

TODO:
    - investigate if parsing just the audio stream for the video is possible within python (pyAv?)
    - do some kind of poll of AoT people to see what video formats they use most
    - need some kind of youtube-to-local video downloader
    - investigate if we can use sphinx train to add in astronomy jargon words into the Sphinx engine
    - make this an actual package
    - convert audio transcription into .srt files
    - figure out how to encode .srt files directly into the video
    - upload the new video back to youtube automatically, so need something to manage credentials
