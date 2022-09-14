
## Tasks  (Replace topic-tag by current topic tag)
```dataview
TASK WHERE contains(text, "#topic-tag")
```
## Permanent notes (Replace topic-tag by current topic tag)
```dataview
Table 
	map(
		filter(
			tags, (x) => startswith(x, "perm")
		),
		(item) => "[" + item + "](obsidian://search?vault=Donaldo&query=tag:%23" + item + ")"
	)
AS "Tags" FROM #topic-tag AND "y) Permanent"
```
