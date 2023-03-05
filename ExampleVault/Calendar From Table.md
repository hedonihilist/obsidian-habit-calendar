```dataview
table habit1 as "Habit1|😊", habit2 as "Habit2|👍"
from "diarys"
```

```dataviewjs
const table = await dv.query(`
table
habit1 as "H1|👍", habit2 as "H2|😊" 
from "diarys"`)
console.log(table)
renderHabitCalendar(this.container, dv, {
	year: 2023,
	month: 2,
	data: table
})
```

```dataviewjs
const table = await dv.query(`
table
choice(habit1,string(habit1)+"min", null) as "H1|👍",
choice(habit2,string(habit2)+"min", null) as "H2|😊" 
from "diarys"`)
console.log(table)
renderHabitCalendar(this.container, dv, {
	year: 2023,
	month: 2,
	data: table
})
```

```dataview
table
habit1, habit2 
from "日记"
```

```dataviewjs
const table = await dv.query(`
table
habit1, habit2 
from "日记"`)
console.log(table)
renderHabitCalendar(this.container, dv, {
	year: 2023,
	month: 3,
	data: table,
	note_pattern: 'YYYY年MM月DD日'
}) 
```
