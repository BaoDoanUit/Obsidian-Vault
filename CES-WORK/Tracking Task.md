```dataview
table 
Link as "Ticket",
Promodos,
"<progress value='" + (length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100 + "' max='100'></progress>"
as "Status",length(filter(file.tasks.completed, (t) => t = true)) AS "Progress" , length(file.tasks) as "Total"
from "CES-WORK/Requirement"
WHERE length(filter(file.tasks.completed, (t) => t = true)) != length(file.tasks)
sort file.ctime desc
```

```dataview
task
from "CES-WORK/Requirement"
where status != "x"
group by file.name
```