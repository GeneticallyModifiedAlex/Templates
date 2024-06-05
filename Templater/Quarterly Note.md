---
creation Date: <% tp.file.creation_date() %>
tags:
  - MonthlyNote
  - <%tp.file.title%>
linklist:
  - "[[ChangeLog]]"
  - '[[<%moment(tp.file.title,"YYYY-[M]MM").format("YYYY")%>]]'
aliases:
  - <%tp.file.title%>
  - <%tp.date.now("MMMM YYYY",0)%>
  - <%tp.date.now("YYYY MMMM",0)%>
---

[[Periodic Notes/4.Quarterly Notes/<%moment(tp.file.title,"YYYY-[Q]Q").subtract(1,'Q').format("YYYY-[Q]Q")%>|Last Month]] 


[[Periodic Notes/4.Quarterly Notes/<%moment(tp.file.title,"YYYY-[Q]Q").add(1,'Q').format("YYYY-[Q]Q")%>|Next Month]]

# Thoughts

## What Happened
## What Have Happened
## What's Next

# Facts

## Files Created

## Tasks Done

## Tasks Left
#PeriodicToDo 
