
Use `date_pattern` to specify the date pattern of your diary. For example, If you are using 'YYYY年MM月DD日'：

```dataviewjs
let pages = dv.pages(`"日记"`)
const year = 2023
const month = 3
const date_pattern = 'YYYY年MM月DD日'
const habit_tag = '#habit'
const habits = {
	'writing': '✍️ x {habit} min',  // this habit will be displayed like '✍️ x 30 min'
	'swim': '🏊 x {habit} min',
}

let data = {}
for (let page of pages) {
	let date = page.file.name
	data[date] = data[date] || ''
	for (let task of page.file.tasks.filter(task => task.tags.contains(habit_tag) && task.checked)) {
		for (let habit in habits) {
			if (task[habit]) {
				data[date] += habits[habit].replace('{habit}', task[habit]) + '\n'
			}
		}
	} 
}

let calendarData = []
for (let date in data) {
	calendarData.push({date: date, content: data[date]})
}
renderHabitCalendar(this.container, dv, {year, month, data: calendarData, date_pattern}) 
```

`date_pattern` can also be applied to table input:


```dataview
table
coding as "Coding|👨‍💻", fishing as "Fishing|🎣"
from "日记"
```

```dataviewjs
const table = await dv.query(`
table
coding as "Coding|👨‍💻", fishing as "Fishing|🎣"
from "日记"
`)
renderHabitCalendar(this.container, dv, {
	year: 2023,
	month: 3,
	data: table,
	date_pattern: 'YYYY年MM月DD日'
}) 
```