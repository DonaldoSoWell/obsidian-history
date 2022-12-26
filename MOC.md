
```button
name Daily
type command
action Daily notes: Open today's daily note
color blue
```
^button-daily


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

 
![[1. Projects]]  
![[2. Areas]]  
> [[3. Resources]]
> [[4. Archives]] 

```dataview 
list from "1. Projects"
```

```dataviewjs 
let title = "Files"; 
let dir = '2. Areas'; 
let processed = [];
function listRecursive(folder, depth) { 
	let files = []; 
	// All pages in the scope of the current path 
	let pages = dv.pages('"' + folder + '"') 
	// Collect files in the current folder here 
	let currentFiles = ""; 
	pages.forEach(page => { 
		if (page.file.folder === folder) { 
			// Page is in current folder 
			currentFiles += page.file.link + " | ";
		} else { 
			// Page is in subfolder 
			let nestedFolder = page.file.folder; 
			// Make sure nested folder is direct child, not any other descendant from current folder 
			let isChild = folder.split('/').length + 1 == nestedFolder.split('/').length; 
			// Make sure we dont process sub-directories multiple times 
			if (!processed.includes(nestedFolder) && isChild) { 
				processed.push(nestedFolder); 
				// Result of recursive call is a list, by adding it to the current list we recursively build a tree 
				files.push(listRecursive(nestedFolder, depth + 1)); 
			} 
		} 
	}); 
	if (currentFiles.endsWith(" | ")) currentFiles = currentFiles.slice(0, -3); 
	// Add files in current folder at the start 
	if (currentFiles !== "") files.unshift(currentFiles); 
	// Add current folder name at the start 
	let path = folder.split('/'); 
	path = path [path.length - 1]; 
	if (depth == 0) path = path; 
	files.unshift("<h3>" + path + "</h3>"); 
	return files; 
} 
let files = listRecursive(dir, 0); 
dv.header(3, title); 
dv.list(files);
```
