# Périgord Habitat
## Tasks
```dataview
TASK WHERE contains(text, "#clients/perigord")
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
AS "Tags" FROM #clients/perigord AND "y) Permanent"
```
