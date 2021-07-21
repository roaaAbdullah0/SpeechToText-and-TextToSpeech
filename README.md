# SpeechToText-and-TextToSpeech
Convert speech to text Convert text to speech using [IBM watson](https://cloud.ibm.com/login?state=%2Fservices%2Fspeech-to-text%2Fcrn%253Av1%253Abluemix%253Apublic%253Aspeech-to-text%253Aeu-gb%253Aa%252F0d02caae845b4f96b3c028f9112348a8%253A8a0fc121-ba80-4864-8045-2b8aa437bfb1%253A%253A%3FpaneId%3Dmanage&sessionExpired=true) and Python language
![](https://i.imgur.com/DWKASYO.jpg)

## Installation
 ```python
   pip install pipwin
   pip3 install pyaudio
   pip install ibm_watson
 ```
## Speech to Text
* change In speech.cfg file apikey and region 
 ```python
apikey = 'v7ygeMt5FhrXBO2fdi8ztBymQNKnyicElXSbm5JkZyoB'

region ='eu-gb'
 ```
* Save and Create text.text file
 ```python
 text= data['results'][0]['alternatives'][0]['transcript']

    with open("text.txt", "w") as out :

    out.write(text)

    out.close()
 ```

## Text To Speech
* change apikey and region in transcribe.py file
```python
apikey = '57uWuMBYbQO9Yel-Ig9GDkNXJE-2DAVFyha1FbbOV7b9'
url = 'https://api.eu-gb.text-to-speech.watson.cloud.ibm.com/instances/88ad59e8-0bad-43f0-b134-476431de07a9'
```
```python
# Setup Service
authenticator = IAMAuthenticator(apikey)
tts = TextToSpeechV1(authenticator=authenticator)
tts.set_service_url(url)
```
```python
with open('text.txt', 'r') as f:
    text = f.readlines()
with open('./speech.mp3', 'wb') as audio_file:
    res = tts.synthesize(text, accept='audio/mp3', voice='en-GB_JamesV3Voice').get_result()
    audio_file.write(res.content)
```
