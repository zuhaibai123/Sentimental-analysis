# Sentimental-analysis
pip  install openai

import openai

openai.api_key = ""

def sentimental_analysis(text):
<br>
  messages= [
      {"role" : "system" ,"content" : """ You are trained the analyze the sentiment of a text.
                                          if your are not sure about the answer say "not sure" and  tell the user to check manually.""" },
        {"role" : "user" , "content" : f"""Analyze the given text and answer if the sentiment is :postive or negative.
                                           Give your answer in one word only as either positive or negative : {text} """}
  ]
  response =  openai.ChatCompletion.create(
                 model="gpt-3.5-turbo",
                 messages = messages ,
                 max_tokens=1,
                 n=1,
                 stop=None,
                 temperature=0)

  response_text= response.choices[0].message.content.strip().lower()
  return response_text
