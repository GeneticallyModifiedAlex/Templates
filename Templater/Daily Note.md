---
creation Date: <% tp.file.creation_date() %>
tags:
  - Daily
  - <%tp.file.title%>
  - <%moment(tp.file.title,"YYYY-MM-DD").format("YYYY-[W]ww")%>
linklist:
  - '[[<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-[W]ww") %>]]'
aliases: 
Totals_Task-Done: 
Totals_Task-ToDo: 
Totals_Task-total: 
Daily_New_task:
---
Days: [[Periodic Notes/1.Daily Notes/<% moment(tp.file.title, "YYYY-MM-DD").subtract(1,'days').format("YYYY-MM-DD") %>|Yesterday]] <-- **[[<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>]]** --> [[Periodic Notes/1.Daily Notes/<% moment(tp.file.title, "YYYY-MM-DD").add(1,'days').format("YYYY-MM-DD") %>|Tomorrow]]

# Today
## Stand Up
>*<% moment(tp.file.title, "YYYY-MM-DD").format("dddd") %>*
> 
> 

## Change Log
Created Today:
```dataview
list
WHERE file.cday = date("<%tp.file.title%>")
sort file.name asc
```
Modified Today(may change due to later modifications):
```dataview
list
WHERE file.mday = date("<%tp.file.title%>") AND file.cday != date("<%tp.file.title%>")
sort file.name asc
```

## ToDo
#PeriodicToDo 
- [ ] #ToDo Update Tasks at [[End Of Day|EOD]] [created:: <% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>]

### Other File ToDo's
```dataview
TASK
WHERE created = date("<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>") OR start = date("<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>") OR scheduled = date("<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>") OR due = date("<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>")
WHERE status != "x" AND status != "-"
WHERE file.name != "<%tp.file.title%>"
WHERE text != "" AND text != "-"

SORT priority DESC
```

## Done
### Completed Today
```dataview
TASK
WHERE completion = date("<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>")
WHERE text != ""

Group By C.day
```

# Past

## Remaining Tasks from Yesterday
```dataview
TASK
WHERE status != "x" AND status != "-"
WHERE created = date("<% moment(tp.file.title, "YYYY-MM-DD").subtract(1,'days').format("YYYY-MM-DD") %>") OR start = date("<% moment(tp.file.title, "YYYY-MM-DD").subtract(1,'days').format("YYYY-MM-DD") %>") OR scheduled = date("<% moment(tp.file.title, "YYYY-MM-DD").subtract(1,'days').format("YYYY-MM-DD") %>")
WHERE text != ""

SORT priority DESC
```

## Remaining Tasks from past Week
```dataview
TASK
WHERE created >= date("<% moment(tp.file.title, "YYYY-MM-DD").startOf('week').format("YYYY-MM-DD") %>") and created <= date("<% moment(tp.file.title, "YYYY-MM-DD").endOf('week').format("YYYY-MM-DD") %>") OR start >= date("<% moment(tp.file.title, "YYYY-MM-DD").startOf('week').format("YYYY-MM-DD") %>") and start <= date("<% moment(tp.file.title, "YYYY-MM-DD").endOf('week').format("YYYY-MM-DD") %>") OR scheduled >= date("<% moment(tp.file.title, "YYYY-MM-DD").startOf('week').format("YYYY-MM-DD") %>") and scheduled <= date("<% moment(tp.file.title, "YYYY-MM-DD").endOf('week').format("YYYY-MM-DD") %>")
WHERE file.name != "<%tp.file.title%>"
WHERE status != "x" AND status != "-"
WHERE text != ""

GROUP BY file.name
SORT created DESC
```
