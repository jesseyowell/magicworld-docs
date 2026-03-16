---
title: A page
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
```html
<a href="https://www.google.com">break me!</a>
```

OK OK!

[block:html]
{
  "html": "<div></div>"
}
[/block]


```python
import audiostack
import os

audiostack.api_key = "APIKEY"


text = """<as:section name="main"> 
  Hey <as:placeholder id="username"> </as:placeholder>. At your local gym in <as:placeholder id="location">location</as:placeholder>, we have a huge range of classes including <as:placeholder id="classes">classes</as:placeholder> for you to enjoy. We're offering 50% off if you reactivate your subscription by the end of the month, just for you. Check out our website now!
</as:section>
"""

print(f"Creating your script...")
script = audiostack.Content.Script.create(scriptText=text)
print(script)

print(f"Generating speech...")
speech = audiostack.Speech.TTS.create(scriptItem=script, audience={"username" : "Peyton", "location" : "Brooklyn", "classes" : "pilates and yoga"}, voice="myra", voiceIntelligence= True)
print(speech)

print(f"Creating your mix...")
mix = audiostack.Production.Mix.create(
        speechItem=speech,
        masteringPreset="podcast",
    )
print(mix)

print(f"Downloading your customised ad...")
mix.download(fileName=f"example_")
print(mix)
```