# Signal

Signal API Automation with Tasker  

## API

install this API on your Homeserver or Cloud instance - <https://github.com/bbernhard/signal-cli-rest-api> using docker

```sh

## Create Folder to store signal key data's
mkdir $HOME/.local/share/signal-cli

## Deploy signal api via docker
docker run -d --name signal-api --restart=always -p 6002:6002 -v $HOME/.local/share/signal-cli:/home/.local/share/signal-cli -e MODE=native -e PORT=6002 -e AUTO_RECEIVE_SCHEDULE="0 22 * * *" bbernhard/signal-cli-rest-api

```

- Link device via QRCODE

```sh
http://localhost:6002/v1/qrcodelink?device_name=tasker
```

- For more about API usage refer this: <https://bbernhard.github.io/signal-cli-rest-api/>
- Live Cricket Score API: <https://github.com/sanwebinfo/cricket-api>  

## Signal API Get cricket score

This task is created according to MIUI you can modify the task end according to your device's OS
because in the end it closes via the app via RAM cleaner MIUI widget so I set autoinput v2 according to the widget placement.  

```sh
Task: Signal API Get Cricket Score
    Comments: Replace the example http api url with your api url 
    Settings: Abort Existing Task
    
    <Read the Notification Title and Text>
    A1: AutoNotification Query [
         Configuration: Notification Apps: Signal
         Timeout (Seconds): 20
         Structure Output (JSON, etc): On ]
    
    <wait for 2 secs to send to reply>
    A2: Wait [
         MS: 0
         Seconds: 2
         Minutes: 0
         Hours: 0
         Days: 0 ]
    
    <Open a Notification>
    A3: AutoNotification Actions [
         Configuration: Notification Apps: Signal
         Intercept Action ID: %antouchaction()
         Timeout (Seconds): 20
         Structure Output (JSON, etc): On ]
    
    <wait for 2 secs to send to reply>
    A4: Wait [
         MS: 0
         Seconds: 2
         Minutes: 0
         Hours: 0
         Days: 0 ]
    
    <Typing indicator>
    A5: HTTP Request [
         Method: PUT
         URL: https://signal.example.com/v1/typing-indicator/+910123456789
         Headers: accept:application/json
         Content-Type:application/json
         Body: { "recipient": "+910123456789" }
         Timeout (Seconds): 30
         Structure Output (JSON, etc): On ]
    
    <Fetch Live cricket score json data>
    A6: HTTP Request [
         Method: GET
         URL: https://cricket.example.com/score/live?id=80019
         Timeout (Seconds): 30
         Structure Output (JSON, etc): On ]
    
    <if condition to validate the Title and Text>
    A7: If [ %antext eq score & %antitle eq John doe ]
    
        <Validate the current live match score>
        A8: If [ %http_data.livescore.current eq Data Not Found ]
    
            <send match status data>
            A9: HTTP Request [
                 Method: POST
                 URL: https://signal.example.com/v2/send
                 Headers: accept:application/json
                 Content-Type:application/json
                 Body: {"message": "Hey %antitle 😃 \n\n🔴 Currently No Live Match\n\n✅ %http_data.livescore.title \n\n📑 Status - %http_data.livescore.update", "number": "+910123456789", "recipients": [ "+910123456789" ]}
                 Timeout (Seconds): 30
                 Structure Output (JSON, etc): On ]
    
        A10: Else
    
            <send live score>
            A11: HTTP Request [
                  Method: POST
                  URL: https://signal.example.com/v2/send
                  Headers: Content-Type:application/json
                  Body: {"message": "%http_data.livescore.title\n\n🔴 Live Score - %http_data.livescore.current\n\n📊 Run Rate - %http_data.livescore.runrate\n\n✊ Current Batsman - %http_data.livescore.batsman - %http_data.livescore.batsmanrun%http_data.livescore.ballsfaced\n\n✊ Current Bowler - %http_data.livescore.bowler - %http_data.livescore.bowlerover Over %http_data.livescore.bowlerruns Run - %http_data.livescore.bowlerwickets Wicket  \n\n📑 Status - %http_data.livescore.update", "number": "+910123456789", "recipients": [ "+910123456789" ]}
                  Timeout (Seconds): 30
                  Structure Output (JSON, etc): On ]
    
        A12: End If
    
    A13: Else
    
        <command warning message>
        A14: HTTP Request [
              Method: POST
              URL: https://signal.example.com/v2/send
              Headers: Content-Type: application/json
              Body: {"message": "Hey %antitle 😃\n\n❎ Enter a Valid Command", "number": "+910123456789", "recipients": [ "+910123456789" ]}
              Timeout (Seconds): 30
              Structure Output (JSON, etc): On ]
    
    A15: End If
    
    <wait for signal message to disappear>
    A16: Wait [
          MS: 0
          Seconds: 5
          Minutes: 0
          Hours: 0
          Days: 0 ]
    <close the app>
    A17: Go Home [
          Page: 0 ]
    
    <wait for signal message to disappear>
    A18: Wait [
          MS: 0
          Seconds: 2
          Minutes: 0
          Hours: 0
          Days: 0 ]
    
    <Clean it>
    A19: AutoInput Actions v2 [
          Configuration: Actions To Perform: click(point,536\,1831)
         Not In AutoInput: true
         Not In Tasker: true
         Separator: ,
         Check Millis: 1000
          Timeout (Seconds): 60
          Structure Output (JSON, etc): On ]
```
