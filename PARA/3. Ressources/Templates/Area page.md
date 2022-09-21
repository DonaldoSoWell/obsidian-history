<%-*
let title = await tp.system.prompt("TItle");
-%>
<%-*
let path = await tp.system.prompt("Path");
-%>
# <%* tR += title %>
## Projects

```dataview
Table 
	map(
		filter(
			tags, (x) => startswith(x, "perm")
		),
		(item) => "[" + item + "](obsidian://search?vault=Donaldo&query=tag:%23" + item + ")"
	)
AS "Tags" FROM #<%* tR += path.replaceAll(' ','-') %>/<%* tR += title.replaceAll(' ','-') %> AND "PARA/1. Projects"
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
AS "Tags" FROM #<%* tR += path.replaceAll(' ','-') %>/<%* tR += title.replaceAll(' ','-') %> AND "PARA/3. Ressources"
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
AS "Tags" FROM #<%* tR += path.replaceAll(' ','-') %>/<%* tR += title.replaceAll(' ','-') %> AND "PARA/4. Archives"
```

<% tp.file.move('/PARA/2. Areas/' + path + '/' + title) %>