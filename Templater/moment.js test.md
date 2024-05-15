Default values
` moment().format()`
Outputs the current DateTime object in the Format:
<%moment().format()%>

You can also parse it a string in the format side to vary the output. The full Formatting options can be seen [here.](https://momentjs.com/docs/#/displaying/)

Given a date in the title 
`moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD")`
<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD").startOf('month') %>

Passing a date in and modifying format
<% moment("2024-03-06", "YYYY-MM-DD").format("YYYY-MM") %>

Results of experimenting 
![[Pasted image 20240306160122.png]]

Given page title, find the start of (time unit) month and output that in the format specified 
<% moment(tp.file.title, "YYYY-MM-DD").startOf('month').format("YYYY-MM-DD") %>
