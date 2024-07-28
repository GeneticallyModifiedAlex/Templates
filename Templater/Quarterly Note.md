---
creation Date: <% tp.file.creation_date() %>
tags:
  - QuarterlyNote
  - <%tp.file.title%>
linklist:
  - "[[ChangeLog]]"
  - '[[<%moment(tp.file.title,"YYYY-[M]MM").format("YYYY")%>]]'
aliases:
  - <%tp.file.title%>
  - <%tp.date.now("MMMM YYYY",0)%>
  - <%tp.date.now("YYYY MMMM",0)%>
---

[[Periodic Notes/4.Quarterly Notes/<%moment(tp.file.title,"YYYY-[Q]Q").subtract(1,'Q').format("YYYY-[Q]Q")%>|Last Quarter]] 


[[Periodic Notes/4.Quarterly Notes/<%moment(tp.file.title,"YYYY-[Q]Q").add(1,'Q').format("YYYY-[Q]Q")%>|Next Quarter]]

# Thoughts

## What Happened
## What Have Happened
## What's Next

# Facts

## Files Created

## Tasks Done
## Tasks Left

#PeriodicToDo 

```dataview
TASK 
WHERE status != "x"
WHERE created >= date("<%moment(tp.file.title,"YYYY-[Q]Q").startOf('quarter').format("YYYY-MM-DD")%>") AND created <= date("<%moment(tp.file.title,"YYYY-[Q]Q").endOf('quarter').format("YYYY-MM-DD")%>") 
WHERE text != ""
Group By file.name 
```
