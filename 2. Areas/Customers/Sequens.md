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
Table file.inlinks, file.inlinks.file.folder 
FROM "1. Projects"
WHERE contains("Customers/Sequens", this.file.inlinks)
SORT file.name
```

```dataview
table 
FROM "1. Projects"
SORT file.name ASC
```
