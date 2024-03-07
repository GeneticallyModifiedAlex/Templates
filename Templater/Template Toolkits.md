---
tags:
  - Template
  - Toolkits
  - 2024-W06
  - 2024-02-10
aliases:
  - Template toolkits
linklist: 
creation Date: 2024-02-06 19:52
---

This file covers the commands and components that are used in each template.
This is based on the [Templater documentation](https://silentvoid13.github.io/Templater/introduction.html) which isn't great. 
I've edited them a bit to be more useful, which requires a bit of fudging the functions. I'll define any functions that are used in the more complicated functions.
# File
## Insert Creation Date of the File
You can specify the [[Date Format]] in the brackets.
```shell
<%tp.file.creation_date()%>
```

## Insert File Title
```shell
<%tp.file.title%>
```
# Date
Insert the current date (date format, offset, reference string, reference string format)
```shell
<%tp.date.now("YYYY-MM-DD",0)%>
<%tp.date.now("YYYY-MM-DD",0,"2023-01-DD","YYYY-MM-DD"%>
```
## Insert Yesterday's Date
I use this in my [[Periodic Notes]] to refer to the last period (typically in a daily note). This works both for the current day and any date in the future or past. Using an exception by passing in the title of the file.
```shell
<%tp.date.now("YYYY-MM-DD",-1,tp.file.title,"YYYY-MM-DD")%>
```
This translates to.
```
current date in format "YYYY-MM-DD", -1 day, OR use the title of the file as a refrence string which is in format "YYYY-MM-DD"
```
The only issue is that the file will default to a generic note and not save to your [[Periodic Notes]] folder.
To fix it you have to specify the path you want.
```shell
[[Periodic Notes/1.Daily Notes/<%tp.date.now("YYYY-MM-DD",-1,tp.file.title,"YYYY-MM-DD")%>|Yesterday]]
```

- [ ] #ToDo figure out how to do semantic referencing to next week etc  [created:: 2024-01-30]  [scheduled:: 2024-03-07]
# Query
All querys exist in a codeblock and require the dataview plugin.
You also need to label the codeblock with the text 'dataview' next to opening 3 `  s (known as tylda key)
## File Management
This section fulfils the goal of identifying [[Notes Created]], one of the main use cases of [[Periodic Notes]]. This allows a true reflection of creation from a traceability view gives context to the tasks created that day.
### Files Created during a Specified Date
The following is intended for the use of periodic notes to list the files that were created during that date. This is useful as it allows future dates to be created ahead of time and still works. This currently only works for Daily notes as the [[#Insert File Title]] only inserts the title and would need more elaborate date handling to work for any other period.
```
list
WHERE file.cday = date("<%tp.file.title%>")
sort file.name asc
```
## Task Management
There is [[Tasks Meta Data]] that we can utilise in our query either using [[Dataview]] or using the [[Tasks Query]] system. 
Note: Some of this [[Tasks Meta Data]] is implicit, but some needs to be toggled on in the Plugin settings.
### Tasks Completed during a Specified Date
This Query outputs the list of tasks that were marked as completed during a specified date.
Note that this requires completion date to be turned on in settings. 
This takes the current date as a reference unless the file title (the reference string) matches the "YYYY-MM-DD" syntax (the reference format)
As an additional check any items where text is empty (the description of the task).
You can additionally use `WHERE status = "X"` instead, but this is unnecessary if you have completion date turned on.
```
TASK
WHERE completion = date("<%tp.date.now("YYYY-MM-DD",0,tp.file.title,"YYYY-MM-DD")%>")
WHERE text != ""

```

### ![[Group By - A Bug that Became a Feature]]
![](https://publish.obsidian.md/modifiedalex/7.Blog+Posts+and+Articles/7.2.Blog+Posts/Group+By+-+A+Bug+that+Became+a+Feature)