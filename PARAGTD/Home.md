# Home
- [[Projects]]  
- [[Areas]]  
- [[Resources]]  
- [[Archive]]

# Next Actions
```dataview
let projects = dv.pages('outgoing([[Projects]])')  
let rows = projects.flatMap(  
page => page.file.tasks  
.filter(t => !t.completed && t.text.includes('#next'))  
.map(task => [page.file.link, task.text.replace('#next', '')]  
)  
)  
dv.table(['Project', 'Next'], rows)
```