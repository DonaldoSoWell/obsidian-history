---
banner: "https://images.unsplash.com/photo-1553484771-cc0d9b8c2b33?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1901&q=80"
cssclass: dashboard
banner_x: 0.5
banner_y: 0.75
---
# Tasks

```button
name Add daily tasks
type command
action Daily notes: Open today's daily note
color blue
```
^button-nivw
## 🔔 Due
```tasks

due before date(tomorrow)
not done  

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
description regex matches /^[A-Za-z]([A-Za-z]{2}|[A-Za-z][0-9]|[0-9]{2})[0-9]{0,6}$/
short mode

```

# Inbox
```dataview
LIST FROM "0) Inbox"
```

# Work
- ![[1) Work]]

# Personal
![[2) Personal]]
