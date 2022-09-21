# Home
- [[1. Projects]]  
- [[2. Areas]]  
- [[3. Resources]]  
- [[4. Archive]]

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
