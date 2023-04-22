# Omniverse-Virtual-Assisstant using Riva Server (with Riva SDK, deployed in Google Cloud) and Audio2Face

## Demo
[![Demo](http://img.youtube.com/vi/kv9QM-SODIM/maxresdefault.jpg)](https://youtu.be/kv9QM-SODIM "Video Title")

## Prerequisites
- Riva Server
- Audio2Face

- In a conda environment(Prefer)
  -  Riva Python Client: https://github.com/nvidia-riva/python-clients
  - Wikipedia APIs
    - https://pypi.org/project/wikipedia/
    - https://pypi.org/project/Wikipedia-API/


<!-- ## Tutorial -->
<!DOCTYPE html>
<html>
  <head>

  </head>
  <body>
    <h1>Tutorial</h1>
    <p>The tutorial is here: <a href="Tutorials.pdf">Tutorial</a>.</p>
  </body>
</html>

## How to Use?
1. Set up the Riva Server and Audio2Face as indicated by the steps in the Tutorial.
2. After step 1 has been set up, launch both the Riva Server and Audio2Face.
3. Fill in the URI in the config.py in the following format: external IP of your Riva Server:Port of your Riva Server. 
    1. For example, if the external IP of the Riva Sever is "12.34.56.789" and the port of the Riva Server is "50050". Then the content in config.py will be 
    > URI = "12.34.56.789:50050"
3. Check if all the prerequisties are configured.
4. Run main.py.



## Inspired by https://github.com/metaiintw/build-an-avatar-with-ASR-TTS-Transformer-Omniverse-Audio2Face
## Limitations: Currently Using the Wikipedia API for NLP Context Query, so it can only handle Q&A questions that can be answer by Wikipedia.


docker run -d --init --ipc=host --gpus '"device=0"' -p 50051:50051 -e LD_PRELOAD= -e RIVA_API_KEY= -e RIVA_API_NGC_ORG= -e RIVA_EULA= -v riva-model-repo:/data --ulimit memlock=-1 --ulimit stack=67108864 --name riva-speech -p 8000 -p 8001 -p 8002 nvcr.io/nvidia/riva/riva-speech:2.10.0 start-riva --riva-uri=0.0.0.0:50051 --asr_service=true --tts_service=true --nlp_service=true