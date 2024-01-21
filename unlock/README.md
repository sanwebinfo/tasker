# Pin unlock 🔓

> Pin unlock 🔓 - Unlock your Android Device Using Tasker and Autoinput.

Unlock your Android Device Using Tasker and Autoinput use autovoice to type a pin in lockscreen and unlock 🔓 the device using Autovoice and Tasker.

**DEMO:** <https://www.youtube.com/shorts/jy-zjiZh0KE>

```sh

    Task: Pin Unlock 🔓
    
    A1: Turn On [
         Block Time (Check Help): 500 ]
    
    A2: Wait [
         MS: 0
         Seconds: 2
         Minutes: 0
         Hours: 0
         Days: 0 ]
    
    A3: AutoInput Actions v2 [
         Configuration: Actions To Perform: swipe(point,540\,2037,up,1000)
         Not In AutoInput: true
         Not In Tasker: true
         Separator: ,
         Check Millis: 1000
         Timeout (Seconds): 60
         Structure Output (JSON, etc): On ]
    
    A4: Wait [
         MS: 0
         Seconds: 2
         Minutes: 0
         Hours: 0
         Days: 0 ]
    
    A5: AutoInput Action [
         Configuration: Type: Text
         Value: 1
         Action : Click
         Timeout (Seconds): 23
         Structure Output (JSON, etc): On ]
    
    A6: AutoInput Action [
         Configuration: Type: Text
         Value: 2
         Action : Click
         Timeout (Seconds): 23
         Structure Output (JSON, etc): On ]
    
    A7: AutoInput Action [
         Configuration: Type: Text
         Value: 3
         Action : Click
         Timeout (Seconds): 23
         Structure Output (JSON, etc): On ]
    
    A8: AutoInput Action [
         Configuration: Type: Text
         Value: 4
         Action : Click
         Timeout (Seconds): 23
         Structure Output (JSON, etc): On ]
    
    A9: [X] Wait [
         MS: 0
         Seconds: 8
         Minutes: 0
         Hours: 0
         Days: 0 ]
    
    A10: [X] Turn Off [
          Dim: On
          Lock: On ]
```
