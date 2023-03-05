

## Summary

```dataviewjs
let pages = dv.pages(`"diarys"`)
const year = 2023
const month = 2

let data = {}
for (let page of pages) {
	let date = page.file.name
	if (!(date in data)) {
		data[date] = ''
	}
	for (let task of page.file.tasks) {
		if (task.tags.contains('#habit') && task.checked && task.reading) { // select only checked habits
			data[date] += `📖x ${task.reading} min\n`
		}
		if (task.tags.contains('#habit') && task.checked && task.jogging) { // select only checked habits
			data[date] += `🏃x ${task.jogging} min\n`
		}
		if (task.tags.contains('#habit') && task.checked && task.wakey) {
			data[date] += '🌞'
		}
	} 
}
let calendarData = []
for (let date in data) {
	calendarData.push({date: date, content: data[date]})
}
renderHabitCalendar(this.container, dv, {year, month, data: calendarData}) 
```

## Reading

```dataviewjs
let files = dv.pages(`"diarys"`)
let sum = 0
for (let file of files) {
	console.log(file)
	for (let task of file.file.tasks) {
		if (task.tags.contains('#habit') && task.checked && task.reading) { // select only checked habits
			sum += task.reading
		}
	} 
}
dv.paragraph(`You read 📖 for **${sum}** min this month`)
console.log(sum)
```

```dataviewjs
let files = dv.pages(`"diarys"`)
let data = []
for (let file of files) {
	console.log(file)
	for (let task of file.file.tasks) {
		if (task.tags.contains('#habit') && task.checked && task.reading) { // select only checked habits
			data.push({date: file.file.name, content: `📖 ${task.reading} min`})
		}
	} 
}
console.log(data)
renderHabitCalendar(this.container, dv, {year: 2023, month: 2, data: data}) 
```

## Jogging

```dataviewjs
let files = dv.pages(`"diarys"`)
let sum = 0
for (let file of files) {
	console.log(file)
	for (let task of file.file.tasks) {
		if (task.tags.contains('#habit') && task.checked && task.jogging) { // select only checked habits
			sum += task.jogging
		}
	} 
}
dv.paragraph(`You 🏃 jogged for **${sum}** min this month`)
```


```dataviewjs
let files = dv.pages(`"diarys"`)
let data = []
for (let file of files) {
	console.log(file)
	for (let task of file.file.tasks) {
		if (task.tags.contains('#habit') && task.checked && task.jogging) { // select only checked habits
			data.push({date: file.file.name, content: `🏃 ${task.jogging} min`})
		}
	} 
}
console.log(data)
renderHabitCalendar(this.container, dv, {year: 2023, month: 2, data: data, filepath: dv.current().file.path, width: "100%"}) 
```

```dataviewjs

```
## Get up early

```dataviewjs
let files = dv.pages(`"diarys"`)
let data = []
for (let file of files) {
	console.log(file)
	for (let task of file.file.tasks) {
		if (task.tags.contains('#habit') && task.checked && task.wakey) {
			data.push({date: file.file.name, content: '🌞'})
		}
	} 
}
console.log(data)
renderHabitCalendar(this.container, dv, {year: 2023, month: 2, data: data, filepath: dv.current().file.path, width: "100%"}) 
```
