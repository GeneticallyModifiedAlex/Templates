---
creation Date: <% tp.file.creation_date() %>
tags:
  - MonthlyNote
  - <%tp.file.title%>
  - <%tp.date.now("MMMM",0)%>
  - <%tp.date.now("YYYY",0)%>
  - <%tp.date.now("YYYY-[Q]Q",0)%>
linklist:
  - "[[ChangeLog]]"
  - "[[<%tp.date.now("YYYY-[Q]Q",0)%>]]"
aliases:
  - <%tp.date.now("MMMM",0)%>
  - <%tp.date.now("MMMM YYYY",0)%>
  - <%tp.date.now("YYYY MMMM",0)%>
---
# Thoughts

## What Happened
## What Should Have Happened
## What's Next

# Facts

## Files Created

## Tasks
```tracker
searchType: frontmatter
searchTarget: Totals_Task-Done, Totals_Task-ToDo
folder: Periodic Notes/1.Daily Notes
startDate: <% moment(tp.file.title, "YYYY-MM-DD").startOf("month").format("YYYY-MM-DD") %>
endDate: <% moment(tp.file.title, "YYYY-MM-DD").endOf("month").format("YYYY-MM-DD") %>

datasetName: Totals_Task-Done, Totals_Task-ToDo

line:
	title: Tasks
	yAxisLabel: Tasks in state
	lineColor: green, red
	fillGap: true
	showLegend: true
```
### Tasks Done

### Tasks Left
#PeriodicToDo
