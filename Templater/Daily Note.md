---
creation Date: <% tp.date.now("YYYY-MM-DD") %>
tags:
  - Daily
  - <%tp.file.title%>
linklist:
  - '[[<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-[W]ww")%>]]'
aliases: 
Totals_Task_Done: <%* let done = app.metadataCache.getTags()['#Done']-%><%done%>
Totals_Task_ToDo: <%* let todo = app.metadataCache.getTags()['#ToDo']-%><%todo%>
Totals_Task_totals: <%* let totals = done + todo-%><%totals%>
Daily_New_task: 0
Daily_DoneTask: 
HoursOfSleep: 
---
>Age: <%* 
let now = moment(tp.file.title,"YYYY-MM-DD");
let pastDate = moment('1999-07-09',"YYYY-MM-DD");
let ageInWeeks = moment.duration(now.diff(pastDate,'weeks'),'weeks').asWeeks();

let years = moment.duration(now.diff(pastDate,'years'),'years').asYears(); pastDate.add(years,'years');

let months = moment.duration(now.diff(pastDate,'months'),'months').asMonths(); pastDate.add(months,'months'); 

let weeks = moment.duration(now.diff(pastDate,'weeks'),'weeks').asWeeks();
pastDate.add(weeks,'weeks');

let days = moment.duration(now.diff(pastDate,'days'),'days').asDays();
%>
><%ageInWeeks%> Weeks and <%days%> Days Old
><%years%> Years <%months%> Months <%weeks%> Weeks <%days%> days Old

# Today
## Stand Up
>*<% moment(tp.file.title, "YYYY-MM-DD").format("dddd") %>*
> 
> 

## Change Log
Created Today:
```dataview
list
WHERE file.cday = date("<%tp.file.title%>")
sort file.name asc
```
Modified Today(may change due to later modifications):
```dataview
list
WHERE file.mday = date("<%tp.file.title%>") AND file.cday != date("<%tp.file.title%>")
sort file.name asc
```

## ToDo
#PeriodicToDo 
- [ ] #ToDo Update Tasks at [[End Of Day|EOD]] [created:: <% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>]

### Other File ToDo's
```dataview
TASK
WHERE created = date("<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>") OR start = date("<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>") OR scheduled = date("<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>") OR due = date("<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>")
WHERE status != "x" AND status != "-"
WHERE file.name != "<%tp.file.title%>"
WHERE text != "" AND text != "-"

SORT priority DESC
```

## Done
### Completed Today
```dataview
TASK
WHERE completion = date("<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>")
WHERE text != ""

Group By C.day
```

# Past

## Remaining Tasks from Yesterday
```dataview
TASK
WHERE status != "x" AND status != "-"
WHERE created = date("<% moment(tp.file.title, "YYYY-MM-DD").subtract(1,'days').format("YYYY-MM-DD") %>") OR start = date("<% moment(tp.file.title, "YYYY-MM-DD").subtract(1,'days').format("YYYY-MM-DD") %>") OR scheduled = date("<% moment(tp.file.title, "YYYY-MM-DD").subtract(1,'days').format("YYYY-MM-DD") %>")
WHERE text != ""

SORT priority DESC
```

## Remaining Tasks from past Week
```dataview
TASK
WHERE created >= date("<% moment(tp.file.title, "YYYY-MM-DD").startOf('week').format("YYYY-MM-DD") %>") and created <= date("<% moment(tp.file.title, "YYYY-MM-DD").endOf('week').format("YYYY-MM-DD") %>") OR start >= date("<% moment(tp.file.title, "YYYY-MM-DD").startOf('week').format("YYYY-MM-DD") %>") and start <= date("<% moment(tp.file.title, "YYYY-MM-DD").endOf('week').format("YYYY-MM-DD") %>") OR scheduled >= date("<% moment(tp.file.title, "YYYY-MM-DD").startOf('week').format("YYYY-MM-DD") %>") and scheduled <= date("<% moment(tp.file.title, "YYYY-MM-DD").endOf('week').format("YYYY-MM-DD") %>")
WHERE created != date("<% moment(tp.file.title, "YYYY-MM-DD").subtract(1,'days').format("YYYY-MM-DD") %>")
WHERE file.name != "<%tp.file.title%>"
WHERE status != "x" AND status != "-"
WHERE text != ""

GROUP BY file.name
SORT created DESC
```
