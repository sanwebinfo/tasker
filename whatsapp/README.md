# WhatsApp

WhatsApp Automations with Tasker

## Whatsapp Bot

✅ Create WhatsApp Bot using Tasker and AutoNotification

✅ Get Live Cricket Score on your WhatsApp by using commands like Telegram bot

✅ Profile and Task XML file Download link in description

WhatsApp Cricket Score Bot👆

### Requirements

- Two mobile phones with WhatsApp (different numbers)
- one number for sending commands and another one for acting like a bot
- Tasker and AutoNotifications
- Live Cricket API Data  - <https://github.com/sanwebinfo/cricket-api> (self-host this API on Vercel)

***Full Project***

```sh
Profile: WhatsApp Score Bot
    Comments: WhatsApp Cricket Score Bot - Replace Title text  ( WhatsApp Contact Name )with yours
     Event: Notification [ Owner Application:WhatsApp Title:WhatsApp Contact Name Text:* Subtext:* Messages:* Other Text:* Cat:* New Only:Off ]
    
    
    
    Enter Task: WhatsApp Cricket Score Bot
    Settings: Abort Existing Task
    
    <Read the Notification Title and Text>
    A1: AutoNotification Query [
         Configuration: Notification Apps: WhatsApp
         Timeout (Seconds): 20
         Structure Output (JSON, etc): On ]
    
    <Fetch Live cricket score json data>
    A2: HTTP Request [
         Method: GET
         URL: https://api.example.com/score/live?id=12345
         Timeout (Seconds): 30
         Structure Output (JSON, etc): On ]
    
    <if condition to validate the Title and Text>
    A3: If [ %antext eq score & %antitle eq WhatsApp Contact Name ]
    
        <Validate the current live match score>
        A4: If [ %http_data.livescore.current eq Data Not Found ]
    
            <wait for 2 secs to send to reply>
            A5: Wait [
                 MS: 0
                 Seconds: 2
                 Minutes: 0
                 Hours: 0
                 Days: 0 ]
    
            <Reply text - Live Cricket Score Data>
            A6: AutoNotification Reply [
                 Configuration: Notification Apps: WhatsApp
                 Reply Text: Hey %antitle 😃 
                 
                 🔴 Currently No Live Match
                 
                 ✅ %http_data.livescore.title 
                 
                 📑 Status - %http_data.livescore.update
                 
                 Cancel Before Replying: true
                 Timeout (Seconds): 10
                 Structure Output (JSON, etc): On ]
    
        A7: Else
    
            <wait for 2 secs to send to reply>
            A8: Wait [
                 MS: 0
                 Seconds: 2
                 Minutes: 0
                 Hours: 0
                 Days: 0 ]
    
            <Reply text - Live Cricket Score Data>
            A9: AutoNotification Reply [
                 Configuration: Notification Apps: WhatsApp
                 Reply Text: %http_data.livescore.title
                 
                 🔴 Live Score - %http_data.livescore.current
                 
                 📊 Run Rate - %http_data.livescore.runrate
                 
                 ✊ Current Batsman - %http_data.livescore.batsman - %http_data.livescore.batsmanrun%http_data.livescore.ballsfaced
                 
                 ✊ Current Bowler - %http_data.livescore.bowler - %http_data.livescore.bowlerover Over %http_data.livescore.bowlerruns Run - %http_data.livescore.bowlerwickets Wicket  
                 
                 📑 Status - %http_data.livescore.update
                 Cancel Before Replying: true
                 Timeout (Seconds): 10
                 Structure Output (JSON, etc): On ]
    
        A10: End If
    
    A11: Else
    
        <If condition not match>
        A12: AutoNotification Reply [
              Configuration: Notification Apps: WhatsApp
             Reply Text: Hey %antitle 😃
             
             ❎ Enter a Valid Command
             
             Cancel Before Replying: true
              Timeout (Seconds): 10
              Structure Output (JSON, etc): On ]
    
    A13: End If
```

***Task***

```sh

Task: WhatsApp Cricket Score Bot
    Comments: Replace WhatsApp Contact Name with yours
    Settings: Abort Existing Task
    
    <Read the Notification Title and Text>
    A1: AutoNotification Query [
         Configuration: Notification Apps: WhatsApp
         Timeout (Seconds): 20
         Structure Output (JSON, etc): On ]
    
    <Fetch Live cricket score json data>
    A2: HTTP Request [
         Method: GET
         URL: https://api.example.com/score/live?id=12345
         Timeout (Seconds): 30
         Structure Output (JSON, etc): On ]
    
    <if condition to validate the Title and Text>
    A3: If [ %antext eq score & %antitle eq WhatsApp Contact Name ]
    
        <Validate the current live match score>
        A4: If [ %http_data.livescore.current eq Data Not Found ]
    
            <wait for 2 secs to send to reply>
            A5: Wait [
                 MS: 0
                 Seconds: 2
                 Minutes: 0
                 Hours: 0
                 Days: 0 ]
    
            <Reply text - Live Cricket Score Data>
            A6: AutoNotification Reply [
                 Configuration: Notification Apps: WhatsApp
                 Reply Text: Hey %antitle 😃 
                 
                 🔴 Currently No Live Match
                 
                 ✅ %http_data.livescore.title 
                 
                 📑 Status - %http_data.livescore.update
                 
                 Cancel Before Replying: true
                 Timeout (Seconds): 10
                 Structure Output (JSON, etc): On ]
    
        A7: Else
    
            <wait for 2 secs to send to reply>
            A8: Wait [
                 MS: 0
                 Seconds: 2
                 Minutes: 0
                 Hours: 0
                 Days: 0 ]
    
            <Reply text - Live Cricket Score Data>
            A9: AutoNotification Reply [
                 Configuration: Notification Apps: WhatsApp
                 Reply Text: %http_data.livescore.title
                 
                 🔴 Live Score - %http_data.livescore.current
                 
                 📊 Run Rate - %http_data.livescore.runrate
                 
                 ✊ Current Batsman - %http_data.livescore.batsman - %http_data.livescore.batsmanrun%http_data.livescore.ballsfaced
                 
                 ✊ Current Bowler - %http_data.livescore.bowler - %http_data.livescore.bowlerover Over %http_data.livescore.bowlerruns Run - %http_data.livescore.bowlerwickets Wicket  
                 
                 📑 Status - %http_data.livescore.update
                 Cancel Before Replying: true
                 Timeout (Seconds): 10
                 Structure Output (JSON, etc): On ]
    
        A10: End If
    
    A11: Else
    
        <If condition not match>
        A12: AutoNotification Reply [
              Configuration: Notification Apps: WhatsApp
             Reply Text: Hey %antitle 😃
             
             ❎ Enter a Valid Command
             
             Cancel Before Replying: true
              Timeout (Seconds): 10
              Structure Output (JSON, etc): On ]
    
    A13: End If

```
