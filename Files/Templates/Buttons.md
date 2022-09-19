
```button
name Add daily tasks
type command
action Daily notes: Open today's daily note
color blue
```
^button-create-daily

```button
name Meeting
type note(function(){return this.inputEl.value}) template
action Meeting
templater true
color purple
```
^button-create-meeting