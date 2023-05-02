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
Audio Bitrate: 160Kbps

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

### Bonus: Game Streaming

OBS Sources: Game Capture + Application Audio Capture  
OBS Plugins: win-capture-audio v2.2.3-beta  
https://obsproject.com/forum/resources/win-capture-audio.1338/  

Always remember to launch  OBS on the same dedicated GPU on which your game is running.   
Do not use integrated video card unless you can run Stream/record and game on it at the same time.   
If you will try, to run OBS and Game on different GPUs - Source: Game Capture  will see and record only black screen.  

If you see black screen in the OBS preview:  Try to fullscreen the game and move around the menu of the game to initialize the OBS preview.

![image](https://user-images.githubusercontent.com/21064622/234254642-4a1475a0-374d-4576-899e-65e1a7bdbf9d.png)

### Example of Game Capture
Game capture is part of OBS software installation.
![image](https://user-images.githubusercontent.com/21064622/234256793-19354c79-be58-4994-a709-78f369943d93.png)

### Example of Application Audio Capture  
This is a OBS plugin and is not part of OBS itself.
![image](https://user-images.githubusercontent.com/21064622/234256664-2ed31f3f-08bd-49ad-80ac-1395aa5b2100.png)



### Bonus: Downloading streamed content

Even if the stream is over, the video is segmented and need to be downloaded and merged into single video.

Use https://github.com/yt-dlp/yt-dlp/releases/tag/2022.10.04

`yt-dlp.exe "https://www.youtube.com/watch?v=ytnc7g-R6y8`


### Launch OBS together with a game

```
@ECHO OFF
setlocal


"C:\Users\Windows10\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Steam\Company of Heroes.url"
REM START /min "" "steam://rungameid/228200"

REM Did not work at all: "C:\Program Files (x86)\Steam\steamapps\common\Company of Heroes Relaunch\RelicCOH.exe"

set processName=RelicCOH.exe

:loop
tasklist /fi "imagename eq %processName%" 2>NUL | find /i "%processName%" >NUL
if not errorlevel 1 goto found
echo Waiting for %processName% to appear...
timeout /t 5 /nobreak >NUL
goto loop

:found
echo %processName% process found.
explorer "https://www.youtube.com/live_dashboard"
timeout /t 30 


REM --minimize-to-try does not work on windows, you have to manually set global settings to start OBS in minimized/try mode.
cd "C:\Program Files\obs-studio\bin\64bit\"
START /MIN "" "C:\Program Files\obs-studio\bin\64bit\obs64.exe" --minimize-to-try --startstreaming 

```


### Fast and efficient streaming

Final settings:

Youtube: RTMP Stream Key 4K and 60FPS

OBS Settings - Stream - Service: Youtube RTMP with Stream Key
OBS Settings - Stream - Service - Server: Primary Youtube ingest server

OBS Settings - Output - Video: 30000kbps
OBS  Settings - Output - Audio: 160kbps

OBS Settings - Video - Base (Canvas) Resolution: 1920x1080
OBS Settings - Video - Common FPS values: 60FPS

OBS - Source - Game Capture - Hook rate: Fastest

