---
creation Date: <% tp.file.creation_date() %>
tags:
  - WeeklyNote
  - <%tp.file.title%>
  - <%tp.date.now("YYYY-[W]ww",0)%>
linklist:
  - "[[<%tp.date.now("YYYY-[M]MM",0)%>]]"
aliases:
---
# ChangLog
```dataview
list WHERE file.cday <= date("<% tp.date.weekday("YYYY-MM-DD", 6)%>") AND file.cday >= date("<% tp.date.weekday("YYYY-MM-DD", 0) %>") sort file.name asc
```
# What Happened
![[<% tp.date.weekday("YYYY-MM-DD", 0) %>#Stand Up]]
![[<% tp.date.weekday("YYYY-MM-DD", 1) %>#Stand Up]]
![[<% tp.date.weekday("YYYY-MM-DD", 2) %>#Stand Up]]
![[<% tp.date.weekday("YYYY-MM-DD", 3) %>#Stand Up]]
![[<% tp.date.weekday("YYYY-MM-DD", 4) %>#Stand Up]]
# Tasks
#PeriodicToDo 
## Remaining From This Week
```dataview
TASK 
WHERE status != "x"
WHERE created >= date("<% tp.date.weekday("YYYY-MM-DD", 0) %>") AND created <= date("<% tp.date.weekday("YYYY-MM-DD", 6)%>") 
WHERE text != ""
Group By file.name 
```
## Done
```dataview
TASK
WHERE completion >= date("<% tp.date.weekday("YYYY-MM-DD", 0) %>") AND completion <= date("<% tp.date.weekday("YYYY-MM-DD", 6)%>") WHERE text != ""
```