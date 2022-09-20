## Tasks 
```dataview
TASK WHERE contains(text, "#tools/heroku")
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
AS "Tags" FROM #tools/heroku AND "Files/Permanent"
```

