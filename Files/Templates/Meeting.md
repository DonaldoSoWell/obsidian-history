<% tp.file.move('Files/Meetings/' + tp.date.now() + ' | ' + (await tp.system.prompt('Subject:','',false))) %>



# Meeting Title
- **Date:** 
- **Attendees:** 

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