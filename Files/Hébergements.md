# Hébergement

## Tasks
```dataview
TASK WHERE contains(text, "#misc/hebergement")
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
AS "Tags" FROM #misc/hebergement AND "y) Permanent"
```
## www.sowell.app

```
Host: Namecheap
DNS: Namecheap
Language: Wordpress
```

## www.sowellapp.com
```
Host: ?
DNS: Namecheap/Netlify
Language: ?
```

## manager.sowellapp.com
```
Host: Netlify
DNS: Namecheap/Netlify
Language: Vue.js
```

## reporter.sowellapp.com
```
Host: Netlify
DNS: Namecheap/Netlify
Language: Vue.js
```

## admin.sowellapp.com
```
Host: Netlify
DNS: Namecheap/Netlify
Language: Vue.js
```

## api.sowellapp.com
```
Host: Heroku
DNS: Namecheap/Netlify
Language: Rails
```
