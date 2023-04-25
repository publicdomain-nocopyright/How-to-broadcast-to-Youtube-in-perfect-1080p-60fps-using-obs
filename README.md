# How-to-broadcast-to-Youtube-in-perfect-1080p-using-obs

Download OBS: https://obsproject.com/

The first part of the trick is using Youtube HLS instead of Default RTMP Stream Key.    
The second part of the trick is using Stream Key instead of Recommended "Login into Youtube's"   
The third part of the trick is using Youtube HLS in the OBS. It is actually supported!   
The final part of the trick is recording screen in 1080p 60 fps and broadcasting it to Youtube in 4K by manually setting resolution in Youtube's Stream Key.  

### Setup a HLS Stream Key on Youtube. (Youtube' Go Live)  
Open Youtube's Go Live: https://www.youtube.com/live_dashboard
### Select Stream Key - Create new Stream Key:  
Streaming protocol: HLS (Advanced)  
Turn on manual settings: Yes  
Resolution: Resolution: 4k (30Mbps)  
Turn on 60 fps option: yes  

![image](https://user-images.githubusercontent.com/21064622/234244621-0833943c-fdaf-4065-8bf7-cf6b0cf1594f.png)


### Use Youtube's Stream Key in OBS

### Finding HLS Stream Service Option in OBS (Youtube - HLS)
![image](https://user-images.githubusercontent.com/21064622/234242637-0c3069bf-24b8-4fa3-baa9-6441d95f308c.png)
![image](https://user-images.githubusercontent.com/21064622/234242910-212b8d30-7d0e-48dc-92d5-5fde2a4a9b75.png)
### Activating Youtube's Stream Key in the Youtube - HLS Service on OBS
![image](https://user-images.githubusercontent.com/21064622/234243582-3947d474-bd4d-4253-b035-777ee7815171.png)

### Paste Youtube's Stream Key into OBS
![image](https://user-images.githubusercontent.com/21064622/234245177-a5fb33a8-1809-40d1-8c81-5f1a781714d5.png)

### Tick "Ignore streaming service setting recommendations"
![image](https://user-images.githubusercontent.com/21064622/234245864-e9051de2-86a2-48fc-b79d-fcfcbb1f7a6a.png)

### Open "Output" settings tab in OBS and increase Video and Audio bitrates
OBS - Settings - Output - Streaming:  
Video Bitrate: 30000Kbps 
Audio Bitrate: 320Kbps

![image](https://user-images.githubusercontent.com/21064622/234246775-f1151274-9bd5-4014-b1d4-2b5b60bec5ca.png)



### Now you are ready to stream to Youtube in 1080p 60FPS
The youtube's video will have video options above 1080p: 1440p and 4K  
But that's just streaming resolution, not the recording resolution your computer will record.  

### To select recording resolution:
OBS - Settings - Video:
Base canvas resolution: 1920x1080
Common FPS value: 60

![image](https://user-images.githubusercontent.com/21064622/234248011-4f62c953-3c1a-4ca2-adc5-1244657f2dbd.png)

### Setup stream Hotkey
I prefer to use `CTRL + ALT + A` to start and stop the stream.


![image](https://user-images.githubusercontent.com/21064622/234248780-c40014df-882a-40d2-823b-edcdd709da55.png)
