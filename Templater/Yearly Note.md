---
creation Date: <% tp.file.creation_date() %>
tags:
  - MonthlyNote
  - <%tp.file.title%>
  - <%tp.date.now("YYYY",0)%>
linklist:
  - "[[Periodic Notes/Yearly Notes/<%tp.date.now("YYYY",-1,tp.file.title,"YYYY")%>|<%tp.date.now("YYYY",-1,tp.file.title,"YYYY")%>]]"
  - "[[Periodic Notes/Yearly Notes/<%tp.date.now("YYYY",0,tp.file.title,"YYYY")%>|<%tp.date.now("YYYY",0,tp.file.title,"YYYY")%>]]"
  - "[[Periodic Notes/Yearly Notes/<%tp.date.now("YYYY",+1,tp.file.title,"YYYY")%>|<%tp.date.now("YYYY",365,tp.file.title,"YYYY")%>]]"
aliases:

---
# Thoughts

## What Happened
## What Have Happened
## What's Next

# Facts

## Files Created
```dataview
list WHERE file.cday <= date("<% tp.date.weekday("YYYY-MM-DD", 6)%>") AND file.cday >= date("<% tp.date.weekday("YYYY-MM-DD", 0) %>") sort file.name asc
```

## Tasks Done

## Tasks Left
#PeriodicToDo 
