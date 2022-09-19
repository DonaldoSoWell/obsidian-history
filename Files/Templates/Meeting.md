# <% (await tp.system.prompt('Sujets:','',false)) %>
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

<% tp.file.move('Files/Meetings/' + tp.date.now() + ' | ' + tp.file.title) %>