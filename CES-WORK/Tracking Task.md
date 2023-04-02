```dataview
Table without ID file.link as "Ticket",
"<progress value='" + (length(filter(file.tasks.completed, (t) => t = true)) / length(file.tasks)) * 100 + "' max='100'></progress>"
as "Status",length(filter(file.tasks.completed, (t) => t = true)) AS "Progress" , length(file.tasks) as "Total",Promodos, file.ctime as "lastest edit"

from "CES-WORK/Requirement"
WHERE length(filter(file.tasks.completed, (t) => t = true)) != length(file.tasks)
sort file.ctime desc
```

```dataview
LIST
Detail
from "CES-WORK/Requirement"
where length(filter(file.tasks.completed, (t) => t = true)) != length(file.tasks)
```

```dataview
task
from "CES-WORK/Requirement"
where !completed
group by file.name
```

