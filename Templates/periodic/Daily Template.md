Tags: #dailyNote
Links: 
___
# <%tp.date.now("YYYY-MM-DD")%>
<< [[<% moment(tp.file.title,'YYYY-MM-DD').add(-1,'days').format("YYYY-MM-DD") %>]] | [[<% moment(tp.file.title,'YYYY-MM-DD').format("YYYY") %>-W<% moment(tp.file.title, "YYYY-MM-DD").add(-1,'days').week() %>]] | [[<% moment(tp.file.title,'YYYY-MM-DD').add(1,'days').format("YYYY-MM-DD") %>]] >>
## Reminders
- ![[<%tp.date.now("YYYY-MM-DD", -1)%>#Improvement for Tomorrow]]
## Journals
### Gratitude
#### Life (3)
- 
#### Personal (3)
- 
## Log
- [ ] <%tp.file.cursor(1)%>
<%* if (tp.date.now("ddd") == "Sun") { %>
- [ ] Make Weekly Note
<%* } %>
<%* if (tp.date.now("D") == 1) { %>
- [ ] Make Monthly Note
<%* } %>
<%* if (tp.date.now("M-D") == "1-1") { %>
- [ ] Make Yearly Note
<%* } %>
## Reflection
### Lingering Feelings, Observations, Thoughts

### Productivity
#### Previous Improvement Effectiveness 
- 
#### Good
- 
#### Bad
**What's one point of pain from today? How did it feel? How can I learn from it?**
- 
#### Improvement for Tomorrow
- 
___
## Today's Notes
```query
line:("Created:: <%tp.date.now("YYYY-MM-DD")%>")
```
___
