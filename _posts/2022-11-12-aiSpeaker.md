# TTS와 STT를 이용한 인공지능 스피커 만들기

```python

import sys, os, time, random

# lib install
###############################################################
try :                                                         #
    import speech_recognition as sr                           #
    from gtts import gTTS                                     #
    import feedparser                                         #
    from playsound import playsound                           #
except ImportError :                                          #
    os.system('python.exe -m pip install --upgrade pip')      #
    os.system('pip install SpeechRecognition')                #
    os.system('pip install gtts')                             #
    os.system('pip install feedparser')                       #
    os.system('pip install playsound==1.2.2')                 #
    sys.exit()                                                #
###############################################################

# TTS(Text to Speech)
###############################################################
def my_tts(text) :                                            #
    print('[AI] : ' + text)                                   #
    tts = gTTS(text = text, lang='ko')                        #
    file_name = 'voice.mp3'                                   #
    tts.save(file_name)                                       #
                                                              #
    p = playsound(file_name, True)                            #
    os.remove(file_name)                                      #
                                                              #
###############################################################

# RSS - google news feed
###############################################################
def my_news() :                                               #
    url = "https://news.google.com/rss?hl=ko&gl=KR&ceid=KR:ko"#
    news_data = []                                            #
    news_rss = feedparser.parse(url)                          #
    for title in news_rss.entries :                           #
        news_data.append(title.title)                         #
    return news_data                                          #
###############################################################

#STT : Speech to Text
#####################################################################################
def callback(rec, audio) :                                                          #
    print("무엇을 도와드릴까요? ")                                                   #
    try :                                                                           #
        speak = rec.recognize_google(audio, language='ko', show_all=True )          #
                                                                                    #
        if speak == [] :                                                            #
            pass                                                                    #
        else :                                                                      #
            ai(str(speak['alternative'][0]['transcript']))                          #
            print("[USER] : " + str(speak['alternative'][0]['transcript']))         #
                                                                                    #
    except sr.UnknownValueError:                                                    #
        print("Google 음성 인식이 오디오를 이해할 수 없습니다.")                      #
    except sr.RequestError as e:                                                    #
        print("Google 음성 인식 서비스에서 결과를 요청할 수 없습니다.; {0}".format(e))#
#####################################################################################

#####################################################################################
def ai(speech) :
    
    if '뉴스' in speech :
        texts = my_news()

        for text in texts[0:2] :
            my_tts(text)
    elif '날씨' in speech :
        my_tts("오늘은 비가 오고 구름이 많습니다. 강보민은 집에서 공부하세요.")
        
    elif '운세' in speech :
        my_tts("오늘의 운세입니다. 최주인이 괴롭힐 확률이 높습니다. 조심하세요.")
    elif '농담' in speech :
        q_list = ["세상에서 가장 비싼 동물은?","내가 화상통화를 안 하는 이유는?", "자도차가 울면?",
                  "도둑이 제일 좋아하는 아이스크림은?", "반성문을 영어로 쓰면?", 
                  "개가 사람을 가르친다는 네 글자로 하면?", "아이스크림이 죽은 이유는?", 
                  "많은 사람을 치료하는 것을 영어로 하면?"]
        a_list = ["백조","뜨거워서", "잉카", "보석바", "글로벌", "개인지도", "차가와서", "매니큐어"]
        rnd = random.randint(0,len(q_list)-1)
        my_tts(q_list[rnd])
        my_tts(a_list[rnd])
        
######################################################################################    

rec = sr.Recognizer()
try :
    mic = sr.Microphone(0)
except :
    os.system('pip install pipwin')                           
    os.system('pipwin install pyaudio')
    os.exit()
    
with mic as source :
    audio = rec.adjust_for_ambient_noise(source)

stop_listening = rec.listen_in_background(mic, callback)

while True :
    time.sleep(0.1)

```
아직 진행중입니다. ^^;;
