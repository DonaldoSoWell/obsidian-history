# Home
- [[Projects]]  
- [[Areas]]  
- [[Resources]]  
- [[Archive]]

# Next Actions
```dataviewjs
let projects = dv.pages('outgoing([[Projects]])')  
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
let projects = dv.pages('outgoing([[Projects]])')  
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


# Areas with not projects
```dataviewjs
let areas = dv.pages('outgoing([[Areas]])')  
let projects = dv.pages('outgoing([[Projects]])')  
let project_links = projects.map(p => p.file.link)  
let no_proj = areas.filter(area =>  
area.file.outlinks.filter(out =>  
project_links.includes(out)  
).length == 0  
).map(x => x.file.link)  
dv.list(no_proj)
```
