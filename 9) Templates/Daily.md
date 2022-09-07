# {{date:YYYY-MM-DD dddd}}

## TODOs

- [x] test ✅ 2022-09-07
- [ ] 

## Tasks Due Today

```dataview

TASK WHERE !completed AND due = date("{{date:YYYY-MM-DD}}") AND text != ""

```

## Tasks Overdue

```dataview

TASK WHERE !completed AND due < date("{{date:YYYY-MM-DD}}")

```

## Tasks Completed Today

```dataview
TASK WHERE completion = date("{{date:YYYY-MM-DD}}") AND due != date("{{date:YYYY-MM-DD}}")
```