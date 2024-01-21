# Telegram

Telegram Automation with Tasker

## Telegram Autoreply

Telegram auto reply to Specific contact using alexa

> Direct reply from auto notification reply not working for telegram notifications so I use this method.

```sh

Profile: Telegram Reply to Specific Contact
     Event: AutoVoice Recognized [ Configuration:Easy Commands: telegram $reply
    Responses: okay replied $reply to telegram ]
    
    
    
    Enter Task: reply telegram
    
    A1: AutoNotification Query [
         Configuration: Persistency Type: Both
         Notification Apps: Telegram
         Timeout (Seconds): 20
         Structure Output (JSON, etc): On ]
    
    A2: AutoNotification Actions [
         Configuration: Notification Apps: Telegram
         Intercept Action ID: %antouchaction()
         Timeout (Seconds): 20
         Structure Output (JSON, etc): On ]
        If  [ %antitle() eq John Doe ]
    
    A3: Wait [
         MS: 0
         Seconds: 2
         Minutes: 0
         Hours: 0
         Days: 0 ]
    
    A4: AutoInput Action [
         Configuration: Type: Text
         Value: Message
         Text to Write : %reply
         Action : Write
         Timeout (Seconds): 23
         Structure Output (JSON, etc): On ]
    
    A5: Wait [
         MS: 0
         Seconds: 3
         Minutes: 0
         Hours: 0
         Days: 0 ]
    
    A6: AutoInput Actions v2 [
         Configuration: Actions To Perform: click(point,1012\,2347)
         Not In AutoInput: true
         Not In Tasker: true
         Separator: ,
         Check Millis: 1000
         Timeout (Seconds): 60
         Structure Output (JSON, etc): On ]
    
    A7: Wait [
         MS: 0
         Seconds: 2
         Minutes: 0
         Hours: 0
         Days: 0 ]
    
    A8: Go Home [
         Page: 0 ]

```
