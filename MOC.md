
> [[1. Projects]]  
> [[2. Areas]]  
> [[3. Resources]]
> [[4. Archives]] 
```button
name Daily
type command
action Daily notes: Open today's daily note
color blue
```
^button-daily

readdle-spark://bl=QTpkb25hbGRvQHNvd2VsbGFwcC5jb207SUQ6OTQ3NDQyNjUwLjgzNjMzNjkuMTY2%0D%0AOTQ5MjEzMTc5MUBlbWFpbC5hcHBsZS5jb207ZUlEOkFBTWtBRE5oT1RFNU5UYzFM%0D%0AVGRrTVRJdE5EazVZeTFoTlRJMUxXSTJNREl6TW1Fek16azVZd0JHQUFBQUFBRDdC%0D%0AZERmTnFRaFM2ZXNFTy9nd0FWWEJ3Q0FhaUhIZ0FnU1Q0Wnowd2F1V0xicEFBQUFB%0D%0AQUVNQUFDQWFpSEhnQWdTVDRaejB3YXVXTGJwQUFPbkZjOEZBQUE9OzI5MjQzNDY3%0D%0ANTA%3D
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

### Tests apple reminder

```apple-reminders
list: Sowell
```
