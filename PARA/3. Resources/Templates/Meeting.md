<%-* 
let title = await tp.system.prompt("Title");
-%>
# <%* tR += title %>

```button
name Home
type link
action obsidian://advanced-uri?vault=Donaldo&filename=Home
color blue
```
^button-home

- **Date:**  <% tp.date.now() %>
- **Attendees:** 
	- 

## Meeting Objective


## Agenda
- 

## Notes and Decisions
- 

## Action Items
- 

---
**Tags :**
- <% (await tp.system.prompt('Tags:','#clients/',false)) %>

<% tp.file.move('Files/Meetings/' + tp.date.now() + ' | ' + title) %>