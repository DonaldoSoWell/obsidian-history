## Tasks 
```dataview
TASK WHERE contains(text, "#perm/hosting")
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
AS "Tags" FROM #perm/hosting AND "Files/Permanent"
```

