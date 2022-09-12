---
banner: "https://images.unsplash.com/photo-1553484771-cc0d9b8c2b33?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1901&q=80"
cssclass: dashboard
banner_x: 0.5
banner_y: 0.75
---
<div class="title" style="color:Sienna">HOME</div>


```dataviewjs
// find dates based on format [[YYYY-MM-DD]]

const findDated = (task)=>{

if( !task.completed ) {

task.link = " " + "[[" + task.path + "|*]]";

task.date="";

const found = task.text.match(/\[\[([12]\d{3}-(0[1-9]|1[0-2])-(0[1-9]|[12]\d|3[01]))\]\]/);

if(found) task.date = moment(found[1]);

return true;

}

}
const myTasks = dv.pages('"3 Projects"').file.tasks.where(t => findDated(t));

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
