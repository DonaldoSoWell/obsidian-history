## Tasks 
```dataview
TASK WHERE contains(text, "#apps/soclean/mobile")
```
## Projects

```dataview
Table 
	map(
		filter(
			tags, (x) => startswith(x, "perm")
		),
		(item) => "[" + item + "](obsidian://search?vault=Donaldo&query=tag:%23" + item + ")"
	)
AS "Tags" FROM #apps/soclean/mobile AND "PARA/1) Projects"
```

