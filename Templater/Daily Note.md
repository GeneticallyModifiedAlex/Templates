---
creation Date: <% tp.file.creation_date() %>
tags:
  - Daily
  - <%tp.file.title%>
  - <% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-[W]ww") %>

linklist:
  - "[[<%tp.date.now("YYYY-[W]ww",0)%>]]"
aliases:
Totals_Task-Done: 
Totals_Task-ToDo:

---

Days: [[Periodic Notes/1.Daily Notes/<%tp.date.now("YYYY-MM-DD",-1,tp.file.title,"YYYY-MM-DD")%>|Yesterday]] <-- **[[<%tp.date.now("YYYY-MM-DD",0,tp.file.title,"YYYY-MM-DD")%>]]** --> [[Periodic Notes/1.Daily Notes/<%tp.date.now("YYYY-MM-DD",1,tp.file.title,"YYYY-MM-DD")%>|Tomorrow]]

# Today
## Stand Up
> *<%tp.date.now("dddd",0,tp.file.title,"YYYY-MM-DD")%>*
> 
## Change Log
```dataview
list
WHERE file.cday = date("<%tp.file.title%>")
sort file.name asc
```
## ToDo
#PeriodicToDo 
- [ ] #ToDo Update Tasks at [[End Of Day|EOD]] [created:: <%tp.date.now("YYYY-MM-DD",0,tp.file.title,"YYYY-MM-DD")%>]
### Other File ToDo's
```dataview
TASK
WHERE created = date("<%tp.date.now("YYYY-MM-DD",0,tp.file.title,"YYYY-MM-DD")%>") OR start = date("<%tp.date.now("YYYY-MM-DD",0,tp.file.title,"YYYY-MM-DD")%>") OR scheduled = date("<%tp.date.now("YYYY-MM-DD",0,tp.file.title,"YYYY-MM-DD")%>") OR due = date("<%tp.date.now("YYYY-MM-DD",0,tp.file.title,"YYYY-MM-DD")%>")
WHERE status != "x" AND status != "-"
WHERE file.name != "<%tp.file.title%>"
WHERE text != "" AND text != "-"

SORT priority DESC
```
## Done
### Completed Today
```dataview
TASK
WHERE completion = date("<%tp.date.now("YYYY-MM-DD",0,tp.file.title,"YYYY-MM-DD")%>")
WHERE text != ""

Group By C.day
```
# Past
## Remaining Tasks from Yesterday
```dataview
TASK
WHERE status != "x" AND status != "-"
WHERE created = date("<%tp.date.now("YYYY-MM-DD",-1,tp.file.title,"YYYY-MM-DD")%>") OR start = date("<%tp.date.now("YYYY-MM-DD",-1,tp.file.title,"YYYY-MM-DD")%>") OR scheduled = date("<%tp.date.now("YYYY-MM-DD",-1,tp.file.title,"YYYY-MM-DD")%>")
WHERE text != ""

SORT priority DESC
```
## Remaining Tasks from past Week
```dataview
TASK
WHERE created >= date("<%tp.date.now("YYYY-MM-DD",-7,tp.file.title,"YYYY-MM-DD")%>") and created <= date("<%tp.date.now("YYYY-MM-DD",-2,tp.file.title,"YYYY-MM-DD")%>") OR start >= date("<%tp.date.now("YYYY-MM-DD",-7,tp.file.title,"YYYY-MM-DD")%>") and start <= date("<%tp.date.now("YYYY-MM-DD",-2,tp.file.title,"YYYY-MM-DD")%>") OR scheduled >= date("<%tp.date.now("YYYY-MM-DD",-7,tp.file.title,"YYYY-MM-DD")%>") and scheduled <= date("<%tp.date.now("YYYY-MM-DD",-2,tp.file.title,"YYYY-MM-DD")%>")
WHERE file.name != "<%tp.file.title%>"
WHERE status != "x" AND status != "-"
WHERE text != ""

GROUP BY file.name
SORT created DESC
```

