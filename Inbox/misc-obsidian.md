## Tasks 
```dataview
TASK WHERE contains(text, "#misc/obsidian")
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
AS "Tags" FROM #misc/obsidian AND "Files/Permanent"
```

