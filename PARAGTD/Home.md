# Home
- [[1. Projects]]  
- [[2. Areas]]  
- [[3. Resources]]  
- [[4. Archives]]


```dataviewjs
// find dates based on format [[YYYY-MM-DD]]
/* 
const findDated = (task)=>{
 if( !task.completed ) {
  task.link = " " + "[[" + task.path + "|*]]";  
  task.date="";
  const found = task.text.match(/\[\[([12]\d{3}-(0[1-9]|1[0-2])-(0[1-9]|[12]\d|3[01]))\]\]/);
  if(found) task.date = moment(found[1]);
  return true;  
 }
}
*/

const findDated = (task)=>{
 if( !task.completed ) {
  task.link = " " + "[[" + task.path + "|*]]";  
  task.date=task.due;
  const found = task.date != null;
  if(found) task.date = moment(found[1]);
  return true;  
 }
}

const myTasks =  dv.pages("").file.tasks.where(t => findDated(t));

dv.header(1,"Overdue");
dv.table(["task","link"], myTasks.filter(t=> moment(t.date).isBefore(moment(),"day")).sort(t=>t.date).map(t=>[t.text, t.link]));


dv.header(1,"Today");
dv.table(["task","link"], myTasks.filter(t=> moment(t.date).isSame(moment(),"day")).sort(t=>t.date).map(t=>[t.text, t.link]));

dv.header(1,"Upcoming");
dv.table(["task","link"], myTasks.filter(t=> moment(t.date).isAfter(moment(),"day")).sort(t=>t.date).map(t=>[t.text, t.link]));

dv.header(1,"Undated");
dv.table(["task","link"], myTasks.filter(t=> !t.date).sort(t=>t.text).map(t=>[t.text, t.link]));

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
