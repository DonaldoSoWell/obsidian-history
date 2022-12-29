
> [[1. Projects]]  
> [[2. Areas]]  
> [[3. Resources]]
> [[4. Archives]] 

## Tasks

### *Due*
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

const overdueTasks = dv.pages('"1. Projects"').file.tasks.where(t => findDated(t)).filter(t=> moment(t.dueDate).isBefore(moment().add(1,'days'),"day")).sort(t=>t.dueDate);

if (overdueTasks.length) {
	dv.taskList(overdueTasks);
} else {
	dv.el('br', '')
}
```

### *Upcoming*
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
const upcomingTasks = dv.pages('"1. Projects"').file.tasks.where(t => findDated(t)).filter(t=> moment(t.dueDate).isAfter(moment(),"day")).sort(t=>t.dueDate)

if (upcomingTasks.length) {
	dv.taskList(upcomingTasks);
} else {
	dv.el('br', '')
}
```

### *Pending*
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
const stuckTasks = dv.pages('"1. Projects"').file.tasks.where(t => findDated(t)).filter(t=> !t.dueDate)
if (stuckTasks.length) {
	dv.taskList(stuckTasks);
} else {
	dv.el('br', '')
}
```