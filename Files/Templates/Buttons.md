
```button
name Home
type link
action obsidian://advanced-uri?vault=Donaldo&filename=Home
color blue
```
^button-home

```button
name Daily
type command
action Daily notes: Open today's daily note
color red
```
^button-daily

```button
name Meeting
type note(function(){return this.inputEl.value}) template
action Meeting
templater true
color purple
```
^button-meeting
