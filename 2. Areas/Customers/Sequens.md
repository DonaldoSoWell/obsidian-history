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
LIST FROM "1. Projects" WHERE endswith(file.outlinks.file.folder, "Sequens") OR endswith(file.inlinks.file.folder, "Sequens") SORT file.name ASC
```


```dataview
TABLE WITHOUT ID file.inlinks AS "Projects" 
FROM "1. Projects" 
WHERE contains()
SORT file.name
```
