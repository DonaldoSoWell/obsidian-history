
- [[1. Projects]]  
- [[2. Areas]]  
- [[3. Resources]]  
- [[4. Archives]]


## Overdue
```dataviewjs
const findDated = (task)=>{
	if( !task.completed) {
		task.dueDate="";
		if('due' in task) task.dueDate = moment(task.due.ts).format('YYYY-MM-DD');
		if (!('parent' in task) || (task.dueDate != "")) return true;
	}
}

// find tasks on projects folder

const overdueTasks = dv.pages('"PARAGTD/1. Projects"').file.tasks.where(t => findDated(t)).filter(t=> moment(t.dueDate).isBefore(moment(),"day")).sort(t=>t.dueDate);

if (todayTasks.length) dv.taskList(overdueTasks);
```
  ##### Daily
```tasks

due before date(tomorrow)
not done
short mode
path includes Daily

```

## Today
```dataviewjs
const findDated = (task)=>{
	if( !task.completed) {
		task.dueDate="";
		if('due' in task) task.dueDate = moment(task.due.ts).format('YYYY-MM-DD');
		if (!('parent' in task) || (task.dueDate != "")) return true;
	}
}

// find tasks on projects folder

const todayTasks = dv.pages('"PARAGTD/1. Projects"').file.tasks.where(t => findDated(t)).filter(t=> moment(t.dueDate).isSame(moment(),"day")).sort(t=>t.dueDate);
if (todayTasks.length) dv.taskList(todayTasks);
```
  ##### Daily
```tasks
due after date(today)
not done  
short mode
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

if (upcomingTasks.length) dv.taskList(upcomingTasks);
```




```dataviewjs
// find dates based on format [[YYYY-MM-DD]] or on Due date
const findDated = (task)=>{
 if( !task.completed) {
  //task.link = " " + "[[" + task.path + "|*]]";
  task.dueDate="";
  const found = task.text.match(/\[\[([12]\d{3}-(0[1-9]|1[0-2])-(0[1-9]|[12]\d|3[01]))\]\]/);
  if(found) task.dueDate = moment(found[1]).format('YYYY-MM-DD');
  if('due' in task) task.dueDate = moment(task.due.ts).format('YYYY-MM-DD');
  if (!('parent' in task) || (task.dueDate != "")) return true;
 }
}

const myTasks =  dv.pages('"PARAGTD/1. Projects"').file.tasks.where(t => findDated(t));

dv.header(1,"Overdue");
dv.el('hr','');
dv.taskList(myTasks.filter(t=> moment(t.dueDate).isBefore(moment(),"day")).sort(t=>t.dueDate));
dv.el('br','');


dv.header(1,"Today");
dv.el('hr','');
dv.taskList(myTasks.filter(t=> moment(t.dueDate).isSame(moment(),"day")).sort(t=>t.dueDate));
dv.el('br','');

dv.header(1,"Upcoming");
dv.el('hr','');
dv.taskList(myTasks.filter(t=> moment(t.dueDate).isAfter(moment(),"day")).sort(t=>t.dueDate));
dv.el('br','');

dv.header(1,"Undated");
dv.el('hr','');
dv.taskList(myTasks.filter(t=> !t.dueDate));
dv.el('br','');

```


# Next Actions
```dataviewjs
let projects = dv.pages('outgoing([[1. Projects]])')  
let rows = projects.flatMap(  
page => page.file.tasks  
.filter(t => !t.completed && t.text.includes('#next'))  
.map(task => [page.file.link, task.text.replace('#next', '')]  
)  
)  
dv.table(['Project', 'Next'], rows)
```
# Stuck projects
```dataviewjs
let projects = dv.pages('outgoing([[1. Projects]])')  
let stuck = projects.filter(page =>  
page.file.tasks.filter(t =>  
!t.completed && (  
t.text.includes('#next') ||  
t.text.includes('#wait')  
)  
).length == 0  
).map(page => page.file.link)  
dv.list(stuck)
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
