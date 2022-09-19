<% const subject = await tp.system.prompt('Subject:','',false)
<% tp.file.move('Files/Meetings/' + tp.date.now() + ' | ' + ( tR += subject) %>

# <
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