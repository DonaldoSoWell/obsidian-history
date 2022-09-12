# {{date:YYYY-MM-DD dddd}}

[[Home]]

## 📆 TODO
- [ ] 

## 🔔 Tasks Due Today
```dataview

TASK WHERE !completed AND due = date("{{date:YYYY-MM-DD}}") AND text != ""

```

## 🆘 Tasks Overdue
```dataview

TASK WHERE !completed AND due < date("{{date:YYYY-MM-DD}}") AND text != ""

```

## ✅ Tasks Completed Today
```dataview
TASK WHERE completion = date("{{date:YYYY-MM-DD}}") AND due != date("{{date:YYYY-MM-DD}}")
```