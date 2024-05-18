---
creation Date: <% tp.file.creation_date() %>
tags:
  - WeeklyNote
  - <%tp.file.title%>
linklist:
  - '[[<%moment(tp.file.title,"YYYY-[W]ww").format("YYYY-[M]MM")%>]]'
aliases:
---
<%moment(tp.file.title,"YYYY-[W]ww").format("YYYY-MM-DD")%>

# ChangLog "
Created:
<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').format("YYYY-MM-DD")%>

<%moment(tp.file.title,"YYYY-[W]ww").endOf('week').format("YYYY-MM-DD")%>

```dataview
list WHERE file.cday <= date("<%moment(tp.file.title,"YYYY-[W]ww").endOf('week').format("YYYY-MM-DD")%>") AND file.cday >= date("<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').format("YYYY-MM-DD")%>") sort file.name asc
```
Modified (May change with later modifications):
```dataview
list 
WHERE (file.mday <= date("<%moment(tp.file.title,"YYYY-[W]ww").endOf('week').format("YYYY-MM-DD")%>") AND file.mday >= date("<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').format("YYYY-MM-DD")%>")) AND (file.cday != (date("<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').format("YYYY-MM-DD")%>") OR date("<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').format("YYYY-MM-DD")%>") OR date("<% tp.date.weekday("YYYY-MM-DD", 0) %>") OR date("<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').add(1,'days').format("YYYY-MM-DD")%>") OR date("<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').add(2,'days').format("YYYY-MM-DD")%>") OR date("<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').add(3,'days').format("YYYY-MM-DD")%>") OR date("<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').add(4,'days').format("YYYY-MM-DD")%>") OR date("<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').add(5,'days').format("YYYY-MM-DD")%>") OR date("<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').add(6,'days').format("YYYY-MM-DD")%>")))

sort file.name asc
```

# What Happened
# Tasks
#PeriodicToDo 
```tracker
searchType: frontmatter
searchTarget: Totals_Task-Done, Totals_Task-ToDo,Totals_Task-total,Daily_New_task
folder: Periodic Notes/1.Daily Notes
startDate: <%moment(tp.file.title,"YYYY-[W]ww").startOf('week').format("YYYY-MM-DD")%>
endDate: <% moment(tp.file.title, "YYYY-[W]ww").endOf('week').format("YYYY-MM-DD") %>

datasetName: Done,ToDo,total,new

line:
	title: Tasks
	yAxisLabel: Tasks in state
	lineColor: green, red, yellow,blue
	showLegend: true
	fillGap: true
	legendPosition:
```

## Remaining From This Week
```dataview
TASK 
WHERE status != "x"
WHERE created >= date("<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').format("YYYY-MM-DD")%>") AND created <= date("<%moment(tp.file.title,"YYYY-[W]ww").endOf('week').format("YYYY-MM-DD")%>") 
WHERE text != ""
Group By file.name 
```

## Done
```dataview
TASK
WHERE completion >= date("<%moment(tp.file.title,"YYYY-[W]ww").startOf('week').format("YYYY-MM-DD")%>") AND completion <= date("<%moment(tp.file.title,"YYYY-[W]ww").endOf('week').format("YYYY-MM-DD")%>") WHERE text != ""
Group By c.date
```
