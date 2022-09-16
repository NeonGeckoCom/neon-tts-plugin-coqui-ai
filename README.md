# NeonAI Coqui AI TTS Plugin
[Mycroft](https://mycroft-ai.gitbook.io/docs/mycroft-technologies/mycroft-core/plugins) compatible
TTS Plugin for Coqui AI Text-to-Speech.

# Languages:
We support all European Union languages such as:

English, Spanish, French, German, Italian, Polish, Ukrainian, \
Dutch, Romanian, Hungarian, Greek, Czech, Swedish, Portuguese, \
Croatian, Bulgarian, Danish, Slovak, Finnish, Lithuanian, \
Slovenian, Latvian, Estonian, Irish, Maltese

Feel free to open an issue to request support of your language. We implement the languages we want and not the ones we can.\
So even Irish and Maltese are not a problem even though they have less than a million native speakers.

# Performance:

 - amd64
    - AMD/Intel-based desktops/laptops
    - 4 cores, RTF = 0.05
    - 1 core,  RTF = 0.15
 - arm64
    - Raspberry Pi 3/4 and Zero 2 with 64-bit Pi OS
    - Raspberry Pi 4, RTF = 0.5

Real-Time Factor(RTF) - the ratio of how long it takes to generate audio to how long the audio is when spoken.

## Storage:

This plugin has a minimum list of dependencies, which in total fit in 900MB on `amd64`, and 300MB on `arm64`.\
Models are installed on the fly, almost instantly after the first TTS request. You don't need to download languages you don't use.\
Each model weighs about 100MB, in total you only need ~4GB to get support for 25 languages.

# Configuration:
```yaml
tts:
    module: coqui
    coqui: {
        cache: true
    }
```
# Requirements:
`sudo apt install espeak-ng`

Necessary for english, greek and some other languages

## Docker

A docker container using [ovos-tts-server](https://github.com/OpenVoiceOS/ovos-tts-server) is available

You can build and run it locally

```bash
docker build . -t coquitts
docker run -p 8080:9666 coquitts
```

use it `http://localhost:8080/synthesize/hello`
