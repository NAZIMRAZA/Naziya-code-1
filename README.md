# Naziya-code-1
this code is a basics structure of A.I or personal assisstance. you can use this code in you pc or laptop easy but first you need to install some basic import file library 

import speech_recognition as sr
import pyttsx3
import pywhatkit
import datetime
import wikipedia

listener = sr.Recognizer()
engine = pyttsx3.init()
voices = engine.getProperty('voices')
engine.setProperty('voices',voices[1].id)

def talk(text):
   engine.say(text)
   engine.runAndWait()
def take_command():
   try:
        with sr.Microphone() as source:
            print('listening....')
            voice = listener.listen(source)
            command = listener.recognize_google(voice)
            command = command.lower()
            if 'naziya' in command:
                command = command.replace('naziya','')
                print(command)
                
    
   except:
            pass
   return command

def run_naziya():
    command = take_command()
    print(command)

    if 'play' in command:
        song = command.replace('play','')
        talk('playing' + song)       
        print('playing')
        pywhatkit.playonyt(song)
    elif 'time' in command:
     time = datetime.datetime.now().strftime('%I:%M %p')
     print(time)
     talk('current time is' + time)
    elif 'who is the' in command:
        person = command.replace('who is the','')
        info = wikipedia.summary(person, 1)
        print(info)
        talk(info)
    elif 'date' in command:
        talk('sorry, i have a headache')
    elif 'are you single' in command:
        talk('I am in a relationship with shagufta') 
    else:
        talk('please say  the command again.')       
 
while True:
  run_naziya()
