---
creation Date: <% tp.file.creation_date() %>
tags:
  - MonthlyNote
  - <%tp.file.title%>
  - <%moment(tp.file.title,"YYYY-[M]MM").format("MMMM")%>
  - <%moment(tp.file.title,"YYYY-[M]MM").format("YYYY")%>
  - <%moment(tp.file.title,"YYYY-[M]mm").format("YYYY-[Q]Q")%>
linklist:
  - "[[ChangeLog]]"
  - "[[<%moment(tp.file.title,"YYYY-[M]MM").format("YYYY-[Q]QQ")%>]]"
aliases:
  - <%moment(tp.file.title,"YYYY-[M]MM").format("MMMM")%>
  - <%moment(tp.file.title,"YYYY-[M]MM").format("MMMM YYYY")%>
  - <%moment(tp.file.title,"YYYY-[M]MM").format("YYYY MMMM")%>
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
