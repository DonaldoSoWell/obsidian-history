---
banner: "https://images.unsplash.com/photo-1553484771-cc0d9b8c2b33?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1901&q=80"
cssclass: dashboard
banner_x: 0.5
banner_y: 0.75
---
# Actions

<div class="row">
  <div class="col-md-6" markdown="1">
  Some text.
  </div>
  <div class="col-md-6" markdown="1">
   Other text
  </div>
</div>

```button
name Add daily tasks
type command
action Daily notes: Open today's daily note
color blue
```
^button-nivw

```button
name Meeting
type note(function(){return this.inputEl.value}) template
action Meeting
templater true
color purple
```
^button-6xsk
## 🔔 Due
```tasks

due before date(tomorrow)
not done
short mode

```
## 🔜 Upcomming
```tasks

due after date(today)
not done  
short mode

```
## ⏳ Unplanned
```tasks

no due date
not done 
exclude sub-items
description regex matches /(?!^$)([^\s])/
short mode

```

# Inbox
```dataview
LIST FROM "Inbox"
```

# Work
- ![[1) Work]]

# Personal
![[2) Personal]]
