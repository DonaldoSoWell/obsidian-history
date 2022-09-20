
<%-*  
let tag = await tp.system.prompt("Tag");  
-%>
## Tasks 
```dataview
TASK WHERE contains(text, "#<% tag %>")
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
AS "Tags" FROM #misc/travaux AND "y) Permanent"
```

```dataview
Table 
	map(
		filter(
			tags, (x) => startswith(x, "perm")
		),
		(item) => "[" + item + "](obsidian://search?vault=Donaldo&query=tag:%23" + item + ")"
	)
AS "Tags" FROM #<%* tag %> AND "Files/Permanent"
```
