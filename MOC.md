
```button
name Daily
type command
action Daily notes: Open today's daily note
color blue
```
^button-daily

## [[1. Projects|🔗 Projects]]
![[1. Projects]]  
## Tasks
### Due
```tasks

due before date(tomorrow)
not done
path includes Daily
hide task count

```
```dataviewjs
const findDated = (task)=>{
	if( !task.completed) {
		task.dueDate="";
		if('due' in task) task.dueDate = moment(task.due.ts).format('YYYY-MM-DD');
		if (!('parent' in task) || (task.dueDate != "")) return true;
	}
}

// find tasks on projects folder

const overdueTasks = dv.pages('"PARA/1. Projects"').file.tasks.where(t => findDated(t)).filter(t=> moment(t.dueDate).isBefore(moment().add(1,'days'),"day")).sort(t=>t.dueDate);

if (overdueTasks.length) {
	dv.taskList(overdueTasks);
} else {
	dv.el('br', '')
}
```




### Upcoming
```tasks
due after date(today)
not done
path includes Daily
hide task count
```  
```dataviewjs

// find dates based on due date
const findDated = (task)=>{
	if( !task.completed) {
		task.dueDate="";
		if('due' in task) task.dueDate = moment(task.due.ts).format('YYYY-MM-DD');
		if (!('parent' in task) || (task.dueDate != "")) return true;
	}
}

// find tasks on projects folder
const upcomingTasks = dv.pages('"PARA/1. Projects"').file.tasks.where(t => findDated(t)).filter(t=> moment(t.dueDate).isAfter(moment(),"day")).sort(t=>t.dueDate)

if (upcomingTasks.length) {
	dv.taskList(upcomingTasks);
} else {
	dv.el('br', '')
}
```



### Pending
```tasks
no due date
not done 
path includes Daily
exclude sub-items
description regex matches /(?!^$)([^\s])/
hide task count
```  
```dataviewjs

// find dates based on due date
const findDated = (task)=>{
	if( !task.completed) {
		task.dueDate="";
		if('due' in task) task.dueDate = moment(task.due.ts).format('YYYY-MM-DD');
		if (!('parent' in task) || (task.dueDate != "")) return true;
	}
}

// find tasks on projects folder
const stuckTasks = dv.pages('"PARA/1. Projects"').file.tasks.where(t => findDated(t)).filter(t=> !t.dueDate)
if (stuckTasks.length) {
	dv.taskList(stuckTasks);
} else {
	dv.el('br', '')
}
```
 

## [[2. Areas|🔗 Areas]]
![[2. Areas]]  

## [[3. Resources|🔗 Resources]] 
![[3. Resources]]  
## [[4. Archives|🔗 Archives]]
![[4. Archives]]


## Areas with no projects
```dataviewjs
let areas = dv.pages('outgoing([[2. Areas]])')  
let projects = dv.pages('outgoing([[1. Projects]])')  
let project_links = projects.map(p => p.file.link)  
let no_proj = areas.filter(area =>  
area.file.outlinks.filter(out =>  
project_links.includes(out)  
).length == 0  
).map(x => x.file.link)  
dv.list(no_proj)
```