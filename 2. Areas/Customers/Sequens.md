---
created_at:
customer_since:
features:
- ..
tags:
- templates/area/customers
---

## Projects 
- [[Connexion SSO Sequens]]

```dataview
LIST FROM "1. Projects" 
WHERE contains("Sequens", this.file.link) 
SORT file.name ASC
```


```dataview
Table file.outlinks, file.outlinks.file.folder, file.inlinks, file.inlinks.file.folder 
FROM "1. Projects"
where contains(file.inlinks, "Sequens")
SORT file.name
```
