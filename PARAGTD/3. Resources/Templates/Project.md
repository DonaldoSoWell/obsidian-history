<%-*  
let title = await tp.system.prompt("Title");  
-%>
<%-*  
let area = await tp.system.prompt("Area");  
-%>

---
tags:
- <%* tR += area %>
---

```button
name Home
type link
action obsidian://advanced-uri?vault=Donaldo&filename=Home
color blue
```
^button-home
## Tasks 
```tasks
heading includes [[<% title %>]]
```

<% await tp.file.move('PARA/1. Projects/' + title) %>