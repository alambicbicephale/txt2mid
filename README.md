# txt2mid

Text to MIDI converter

## What's this ?

This little tool called txt2mid takes a text file as input and outputs a MIDI file with the exact same name + ".mid". The text file has to be written with some simple rules which are described below.

## Text file syntax 

### Add a new note

`<esp>` stands for one blank space 

```
N <esp> date <esp> octave <esp> note <esp> velocity <esp> duration <esp> track
```

* 0 <= note <= 11
* 0 <= velocity <= 127
* the track number begins with 1 (and not with 0)
* date and duration use this rule : quarter note = 240

### Add a new controller change event
```
C <esp> date <esp> cc <esp> value <esp> track
```
* 0 <= cc <= 127
* 0 <= value <= 127
* same other settings as for the notes

### Add a pitchwheel change event
```
P <esp> date <esp> value <esp> track
```
* 0 <= value <= 16383 (middle = 8192)

### Add a note from a frequency [experimental]
works with a pitch bend range of 200 cents
```
H <esp> date <esp> frequency <esp> velocity <esp> duration <esp> track
```
* 30 <= frequency in Hz <= 8346
* same other settings as for the notes

### Add a comment
```
_ commentaire bla bla bla _
```

### Hacks [experimental]
Have to be at the very begining of the text file

#### # ja_spectral
* let use the spectral notation developed by Jamil Alioui
