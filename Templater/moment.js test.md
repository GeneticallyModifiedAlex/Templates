
Default values
` moment().format()`
Outputs the current DateTime object in the Format:
<%moment().format()%>

You can also parse it a string in the format side to vary the output. The full Formatting options can be seen [here.](https://momentjs.com/docs/#/displaying/)

Given a date in the title 
`moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD")`
<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>

Passing a date in and modifying format
<% moment("2024-03-06", "YYYY-MM-DD").format("YYYY-MM") %>

Results of experimenting ![[Pasted image 20240306160122.png]]

---
<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-[W]ww") %>

<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM-DD") %>

subtract / add
<% moment(tp.file.title, "YYYY-MM-DD").subtract(1,'days').format("YYYY-MM-DD") %>
<% moment(tp.file.title, "YYYY-MM-DD").add(1,'days').format("YYYY-MM-DD") %>

start of/ end of
<% moment(tp.file.title, "YYYY-MM-DD").startOf('week').format("YYYY-MM-DD") %>
<% moment(tp.file.title, "YYYY-MM-DD").endOf('week').format("YYYY-MM-DD") %>
