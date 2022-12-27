
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

un mail
[Réponse automatique : Sylvie MENARD a émis un nouveau signalement](message:%3Cbc892136144747d4b35483ec17bc97be@MR1P264MB4321.FRAP264.PROD.OUTLOOK.COM%3E)
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