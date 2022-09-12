---
banner: "https://images.unsplash.com/photo-1553484771-cc0d9b8c2b33?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1901&q=80"
cssclass: dashboard
banner_x: 0.5
banner_y: 0.75
---
<div class="title" style="color:Sienna">HOME</div>


```dataviewjs
const myTasks = dv.taskList(dv.pages().file.tasks.where(t => !t.completed));

dv.header(2,"Overdue");
dv.taskList(myTasks.filter(t=> moment(t.date).isBefore(moment(),"day")).sort(t=>t.date));

dv.header(2,"Today");
dv.taskList(myTasks.filter(t=> moment(t.date).isSame(moment(),"day")).sort(t=>t.date));

dv.header(2,"Upcoming");
dv.taskList(myTasks.filter(t=> moment(t.date).isAfter(moment(),"day")).sort(t=>t.date));
```

# Tasks

```button
name Add daily tasks
type command
action Daily notes: Open today's daily note
color blue
```
^button-nivw

## 🔔 Due Today
```dataview

TASK WHERE !completed AND due = date("{{date:YYYY-MM-DD}}") AND text != ""

```

## 🆘 Overdue
```dataview

TASK WHERE !completed AND due < date("{{date:YYYY-MM-DD}}") AND text != ""

```

# Work
- ![[1) Work]]

# Personal
![[2) Personal]]
