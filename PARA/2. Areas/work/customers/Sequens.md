# Sequens

```button
name Home
type link
action obsidian://advanced-uri?vault=Donaldo&filename=Home
color blue
```
^button-home
## Projects

```dataview
Table 
FROM #work/customers/Sequens AND "PARA/1. Projects"
```

## Ressources

```dataview
Table 
	map(
		filter(
			tags, (x) => startswith(x, "perm")
		),
		(item) => "[" + item + "](obsidian://search?vault=Donaldo&query=tag:%23" + item + ")"
	)
AS "Tags" FROM #work/customers/Sequens AND "PARA/3. Ressources"
```

## Archives

```dataview
Table 
	map(
		filter(
			tags, (x) => startswith(x, "perm")
		),
		(item) => "[" + item + "](obsidian://search?vault=Donaldo&query=tag:%23" + item + ")"
	)
AS "Tags" FROM #work/customers/Sequens AND "PARA/4. Archives"
```

