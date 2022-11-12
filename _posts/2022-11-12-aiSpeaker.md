# TTS와 STT를 이용한 인공지능 스피커 만들기

```python

import speech_recognition as sr
from gtts import gTTS
import feedparser, os, time
from pygame import mixer

def myNews() :
    news_data = []
    news_rss = feedparser.parse("https://news.google.com/rss?hl=ko&gl=KR&ceid=KR:ko")
    for title in news_rss.entries :
        news_data.append(title.title)
    return news_data

def myTts(speech) :
    print('[인공지능 AI] : ' + speech)
    tts = gTTS(text = speech, lang='ko')
    file = 'voice.mp3'
    tts.save(file)

    mixer.init()
    mixer.music.load(file)
    mixer.music.play()
    
    while True :
        if mixer.music.get_busy() == 0 :
            mixer.music.unload()
            os.remove(file)
            break
        else :
            time.sleep(0.1)

def ai(mySpeech) :
    if '뉴스' in mySpeech :
        count = 1
        for n in myNews()[0:5] :
            myTts("{0}번째 뉴스입니다.".format(count) + n)
            count += 1
    elif '운세' in mySpeech :
        myTts("오늘의 운세입니다. 행운과 복이 충만한 하루입니다.")
        pass
    elif '날씨' in mySpeech :
        myTts("오늘의 날씨는 맑고 화창한 날입니다. 가족들과 나들이 가세요.")
        pass

def callback(r, audio) :
    print("무엇을 도와드릴까요? ")
    try :
        speak = r.recognize_google(audio, language='ko', show_all=True )
        if speak == [] :
            pass
        else :
            ai(str(speak['alternative'][0]['transcript']))
            #print(str(speak['alternative'][0]['transcript']))
        #print(recognizer.recognize_google(audio, language='ko'))
    
    except sr.UnknownValueError:
        print("Google 음성 인식이 오디오를 이해할 수 없습니다.")
    except sr.RequestError as e:
        print("Google 음성 인식 서비스에서 결과를 요청할 수 없습니다.; {0}".format(e))

r = sr.Recognizer()
m = sr.Microphone(0)
with m as source :
    audio = r. adjust_for_ambient_noise(source)
    
stop_listening = r.listen_in_background(m, callback)

while True :
    time.sleep(0.1)
```
아직 진행중입니다. ^^;;
