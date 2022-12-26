---
created_at:
customer_since:
features:
- ..
tags:
- templates/area/customers
---

## Projects 
```dataview
LIST
FROM "1. Projects" and outgoing([[Sequens]])
SORT file.name ASC
```

```dataview
table 
file.link, file.inlinks, file.outlinks
```
