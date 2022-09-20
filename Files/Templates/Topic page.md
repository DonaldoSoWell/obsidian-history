
<%-*  
let title = await tp.system.prompt("Title");  
-%>
## Tasks 
```dataview
TASK WHERE contains(text, "#<%* tR += title %>")
```
## Permanent notes

```dataview
Table 
	map(
		filter(
			tags, (x) => startswith(x, "perm")
		),
		(item) => "[" + item + "](obsidian://search?vault=Donaldo&query=tag:%23" + item + ")"
	)
AS "Tags" FROM #<%* tR += title %> AND "Files/Permanent"
```