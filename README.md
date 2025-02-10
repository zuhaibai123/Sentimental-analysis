# Sentimental-analysis
pip  install openai

import openai

openai.api_key = ""

def sentimental_analysis(text):
<br>
  messages= [
  <br>
      {"role" : "system" ,"content" : """ You are trained the analyze the sentiment of a text.
                                          if your are not sure about the answer say "not sure" and  tell the user to check manually.""" },
       <br>                                   
        {"role" : "user" , "content" : f"""Analyze the given text and answer if the sentiment is :postive or negative.
                                           Give your answer in one word only as either positive or negative : {text} """}
                                           <br>
  ]
  <br>
  response =  openai.ChatCompletion.create(
  <br>
                 model="gpt-3.5-turbo",
                  <br>
                 messages = messages ,
                  <br>
                 max_tokens=1,
                  <br>
                 n=1,
                  <br>
                 stop=None,
                 <br>
                 temperature=0)
                  <br>

  response_text= response.choices[0].message.content.strip().lower()
   <br>
  return response_text
