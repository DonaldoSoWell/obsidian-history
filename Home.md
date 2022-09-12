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

## 🆘 Overdue
```dataview

TASK WHERE (status != "x") AND (status != "X") AND (status != "-") AND status != "I" AND status != "/" AND status != ">" AND (due != "") AND (due < date(yesterday)) AND text != ""

```

```tasks

due before date(today)
not done  

```
## 🔔 Due Today
```tasks

due on date(today)
not done  
short mode

```
## 🔜 Upcomming
```dataview
TASK WHERE !completed AND due > date(today) AND text != "" SORT due ASC 
```

```tasks

due after date(today)
not done  

```
## ⏳ Pending
```tasks

no due date
not done 
short mode

```
# Work
- ![[1) Work]]

# Personal
![[2) Personal]]
