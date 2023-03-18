
## Summary

```dataviewjs
let pages = dv.pages(`"diarys"`)
const year = {{date:YYYY}}
const month = {{date:M}}
const date_pattern = 'YYYY-MM-DD'
const habit_tag = '#habit'
const habits = {
	'reading': '📖 x {habit} min',  // this habit will be displayed like '📖 x 30 min'
	'jogging': '🏃 x {habit} min',
	'wakey': '🌞',
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


## Reading

```dataviewjs
let files = dv.pages(`"diarys"`)
const year = {{date:YYYY}}
const month = {{date:M}}
const habit = 'reading'
let sum = 0

for (let file of files) {
	let date = moment(file.file.ctime)
	if (date.year() != year || date.month() != month) {
		continue
	}
	for (let task of file.file.tasks) {
		if (task.tags.contains('#habit') && task.checked && task[habit]) { // select only checked habits
			sum += task[habit]
		}
	} 
}
dv.paragraph(`You read 📖 for **${sum}** min this month`)
```

```dataviewjs
let files = dv.pages(`"diarys"`)
const habit = 'reading'
const year = {{date:YYYY}}
const month = {{date:M}}
const habit_str = '📖 {habit} min'

let data = []
for (let file of files) {
	console.log(file)
	for (let task of file.file.tasks) {
		if (task.tags.contains('#habit') && task.checked && task[habit]) { // select only checked habits
			data.push({date: file.file.name, content: habit_str.replace('{habit}', task[habit])})
		}
	} 
}
console.log(data)
renderHabitCalendar(this.container, dv, {year, month, data}) 
```

## Jogging

```dataviewjs
let files = dv.pages(`"diarys"`)
const year = {{date:YYYY}}
const month = {{date:M}}
const habit = 'jogging'
let sum = 0

for (let file of files) {
	let date = moment(file.file.ctime)
	if (date.year() != year || date.month() != month) {
		continue
	}
	for (let task of file.file.tasks) {
		if (task.tags.contains('#habit') && task.checked && task[habit]) { // select only checked habits
			sum += task[habit]
		}
	} 
}
dv.paragraph(`You 🏃 jogged for **${sum}** min this month`)
```

```dataviewjs
let files = dv.pages(`"diarys"`)
const habit = 'jogging'
const year = {{date:YYYY}}
const month = {{date:M}}
const habit_str = '🏃 {habit} min'

let data = []
for (let file of files) {
	console.log(file)
	for (let task of file.file.tasks) {
		if (task.tags.contains('#habit') && task.checked && task[habit]) { // select only checked habits
			data.push({date: file.file.name, content: habit_str.replace('{habit}', task[habit])})
		}
	} 
}
console.log(data)
renderHabitCalendar(this.container, dv, {year, month, data}) 
```


## Get up early

```dataviewjs
let files = dv.pages(`"diarys"`)
const habit = 'wakey'
const year = {{date:YYYY}}
const month = {{date:M}}
const habit_str = '🌞'

let data = []
for (let file of files) {
	console.log(file)
	for (let task of file.file.tasks) {
		if (task.tags.contains('#habit') && task.checked && task[habit]) { // select only checked habits
			data.push({date: file.file.name, content: habit_str.replace('{habit}', task[habit])})
		}
	} 
}
console.log(data)
renderHabitCalendar(this.container, dv, {year, month, data}) 
```
