
---
tags:
- <%* tR += area %>
---
<%-*  
let title = await tp.system.prompt("Title");  
-%>
_<%-_  
let area = await tp.system.prompt("Area");  
-%>


## Tasks 
```tasks
heading includes [[<% title %>]]
```

<% await tp.file.move('PARA/1. Projects/' + title) %>