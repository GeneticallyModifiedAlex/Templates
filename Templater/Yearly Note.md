---
creation Date: <% tp.file.creation_date() %>
tags:
  - MonthlyNote
  - <%tp.file.title%>
linklist:
  - "[[Periodic Notes/5.Yearly Notes/<% moment(tp.file.title, "YYYY").subtract(1,'years').format("YYYY") %>|<% moment(tp.file.title, "YYYY").subtract(1,'years').format("YYYY") %>]]"
  - "[[Periodic Notes/5.Yearly Notes/<%tp.file.title%>|<%tp.file.title%>]]"
  - "[[Periodic Notes/5.Yearly Notes/<% moment(tp.file.title, "YYYY").add(1,'years').format("YYYY") %>|<% moment(tp.file.title, "YYYY").add(1,'years').format("YYYY") %>]]"
aliases:

---

# Thoughts

## What Happened
## What Have Happened
## What's Next

# Facts
<% moment(tp.file.title, "YYYY").startOf('year').format("YYYY-MM-DD") %>
<% moment(tp.file.title, "YYYY-MM-DD").endOf('week').format("YYYY-MM-DD") %>

## Files Created
```dataview
list WHERE file.cday <= date("<% moment(tp.file.title, "YYYY").endOf('year').format("YYYY-MM-DD") %>") AND file.cday >= date("<% moment(tp.file.title, "YYYY").startOf('year').format("YYYY-MM-DD") %>") sort file.name asc
```

## Tasks Done
```dataview
TASK
WHERE completion >= date("<%moment(tp.file.title,"YYYY").startOf('year').format("YYYY-MM-DD")%>") AND completion <= date("<%moment(tp.file.title,"YYYY").endOf('year').format("YYYY-MM-DD")%>") WHERE text != ""
Group By c.date
```

## Tasks Left
#PeriodicToDo 
```dataview
TASK 
WHERE status != "x"
WHERE created >= date("<%moment(tp.file.title,"YYYY").startOf('year').format("YYYY-MM-DD")%>") AND created <= date("<%moment(tp.file.title,"YYYY").endOf('year').format("YYYY-MM-DD")%>") 
WHERE text != ""
Group By file.name 
```
