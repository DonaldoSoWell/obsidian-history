# Projects
![[1. Projects]]  
# Areas
![[2. Areas]]  
![[3. Resources]]  
![[4. Archives]]

# Tasks
## Due
```dataviewjs
const findDated = (task)=>{
	if( !task.completed) {
		task.dueDate="";
		if('due' in task) task.dueDate = moment(task.due.ts).format('YYYY-MM-DD');
		if (!('parent' in task) || (task.dueDate != "")) return true;
	}
}

// find tasks on projects folder

const overdueTasks = dv.pages('"PARAGTD/1. Projects"').file.tasks.where(t => findDated(t)).filter(t=> moment(t.dueDate).isBefore(moment().add(1,'days'),"day")).sort(t=>t.dueDate);

if (overdueTasks.length) {
	dv.taskList(overdueTasks);
} else {
	dv.el('br', '')
}
```
  ##### Daily
```tasks

due before date(tomorrow)
not done
path includes Daily

```

## Upcoming
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
const upcomingTasks = dv.pages('"PARAGTD/1. Projects"').file.tasks.where(t => findDated(t)).filter(t=> moment(t.dueDate).isAfter(moment(),"day")).sort(t=>t.dueDate)

if (upcomingTasks.length) {
	dv.taskList(upcomingTasks);
} else {
	dv.el('br', '')
}
```
  ##### Daily
```tasks
due after date(today)
not done
path includes Daily
```  

## Stuck
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
const stuckTasks = dv.pages('"PARAGTD/1. Projects"').file.tasks.where(t => findDated(t)).filter(t=> !t.dueDate)
if (stuckTasks.length) {
	dv.taskList(stuckTasks);
} else {
	dv.el('br', '')
}
```
  ##### Daily
```tasks
no due date
not done 
exclude sub-items
description regex matches /(?!^$)([^\s])/
```  
# Areas with no projects
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
