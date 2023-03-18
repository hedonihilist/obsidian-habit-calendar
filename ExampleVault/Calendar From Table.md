Grab a table with habit as column

```dataview
table coding as "Coding|👨‍💻", swim as "Swimming|🏊"
from "diarys"
```
Copy the dataview and pass the query result to HabitCalendar:

```dataviewjs
const table = await dv.query(`
table coding as "Coding|👨‍💻", swim as "Swimming|🏊"
from "diarys"
`)
console.log(table)
renderHabitCalendar(this.container, dv, {
	year: 2023,
	month: 2,
	data: table
})
```

If you'd like it to show the units, change the DQL:

```dataviewjs
const table = await dv.query(`
table
choice(coding,string(coding)+" min", null) as "Coding|👨‍💻",
choice(swim,string(swim)+" min", null) as "Swimming|🏊" 
from "diarys"
`)
console.log(table)
renderHabitCalendar(this.container, dv, {
	year: 2023,
	month: 2,
	data: table
})
```
