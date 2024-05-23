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
  - '[[Periodic Notes/4.Quarterly Notes/<% moment(tp.file.title, "YYYY-[M]MM").format("YYYY-[Q]Q") %>|<% moment(tp.file.title, "YYYY-[M]MM").format("YYYY-[Q]Q") %>]]'
aliases:
  - <%moment(tp.file.title,"YYYY-[M]MM").format("MMMM")%>
  - <%moment(tp.file.title,"YYYY-[M]MM").format("MMMM YYYY")%>
  - <%moment(tp.file.title,"YYYY-[M]MM").format("YYYY MMMM")%>
---
[[Periodic Notes/3.Monthly Notes/<%moment(tp.file.title,"YYYY-[M]MM").subtract(1,'months').format("YYYY-[M]MM")%>|Last Month]] 


[[Periodic Notes/3.Monthly Notes/<%moment(tp.file.title,"YYYY-[M]MM").add(1,'months').format("YYYY-[M]MM")%>|Next Month]]

# Thoughts

## What Happened
## What Should Have Happened
## What's Next

# Facts

## Files Created
## Tasks
```tracker
searchType: frontmatter
searchTarget: Totals_Task_Done, Totals_Task_ToDo
folder: Periodic Notes/1.Daily Notes
startDate: <% moment(tp.file.title, "YYYY-[M]MM").startOf("month").format("YYYY-MM-DD") %>
endDate: <% moment(tp.file.title, "YYYY-[M]MM").endOf("month").format("YYYY-MM-DD") %>

datasetName: Totals_Task_Done, Totals_Task_ToDo

line:
	title: Tasks
	yAxisLabel: Tasks in state
	lineColor: green, red
	fillGap: true
	showLegend: true
```

```tracker
searchType: frontmatter
searchTarget: Daily_New_task
folder: Periodic Notes/1.Daily Notes
startDate: <% moment(tp.file.title, "YYYY-[M]MM").startOf("month").format("YYYY-MM-DD") %>
endDate: <% moment(tp.file.title, "YYYY-[M]MM").endOf("month").format("YYYY-MM-DD") %>

datasetName: Daily_New_task

line:
	title: Tasks
	yAxisLabel: Tasks in state
	lineColor: blue
	fillGap: true
	showLegend: true
```

### Tasks Left
#PeriodicToDo 
```dataview
TASK 
WHERE status != "x"
WHERE created >= date("<%moment(tp.file.title,"YYYY-[M]MM").startOf('month').format("YYYY-MM-DD")%>") AND created <= date("<%moment(tp.file.title,"YYYY-[M]MM").endOf('month').format("YYYY-MM-DD")%>") 
WHERE text != ""
Group By file.name 
```

### Tasks Done
```dataview
TASK
WHERE completion >= date("<%moment(tp.file.title,"YYYY-[M]MM").startOf('month').format("YYYY-MM-DD")%>") AND completion <= date("<%moment(tp.file.title,"YYYY-[M]MM").endOf('month').format("YYYY-MM-DD")%>") WHERE text != ""
Group By c.date
```
