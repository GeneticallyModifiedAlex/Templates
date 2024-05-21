<%*
const tag = "#Done";
const filteredFiles = 
app.vault.getMarkdownFiles().filter(file => {
  const tags = tp.obsidian.getAllTags(app.metadataCache.getFileCache(file));
  return tags;
});
const tagCount = filteredFiles;
-%>
<%tagCount%>

```
filtered files = all markdown files, filtered by the ones that include tags
take the file objects and give a count
```



```
const tag = "#Done";
const filteredFiles = 
app.vault.getMarkdownFiles().filter(file => {
  const tags = tp.obsidian.getAllTags(app.metadataCache.getFileCache(file));
  return tags.includes(tag);
});
const tagCount = filteredFiles.length;
```


<%* let out = app.metadataCache.getTags()['#Done']-%>
<%out%>
