---
creation Date: <% tp.file.creation_date() %>
tags:
  - WeeklyNote
  - <%tp.file.title%>
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
```tracker
searchType: frontmatter
searchTarget: Totals_Task-Done, Totals_Task-ToDo
folder: Periodic Notes/1.Daily Notes
startDate: <% tp.date.weekday("YYYY-MM-DD", 0) %>
endDate: <% tp.date.weekday("YYYY-MM-DD", 6)%>

datasetName: Totals_Task-Done, Totals_Task-ToDo

line:
	title: Tasks
	yAxisLabel: Tasks in state
	lineColor: green, red
	showLegend: true
	fillGap: true
	legendPosition:
```
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
Group By c.date
```