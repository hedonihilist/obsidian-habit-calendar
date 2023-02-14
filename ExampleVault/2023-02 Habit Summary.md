
## Summary

```dataviewjs
let files = dv.pages(`"diarys"`)
let data = {}
for (let file of files) {
	let date = file.file.name
	if (!(date in data)) {
		data[date] = ''
	}
	for (let task of file.file.tasks) {
		if (task.tags.contains('#habit') && task.checked && task.reading) { // select only checked habits
			data[date] += '📖'
		}
		if (task.tags.contains('#habit') && task.checked && task.jogging) { // select only checked habits
			data[date] += '🏃'
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
renderHabitCalendar(this.container, {year: 2023, month: 2, entries: calendarData, filepath: dv.current().file.path, width: "100%"}) 
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
renderHabitCalendar(this.container, {year: 2023, month: 2, entries: data, filepath: dv.current().file.path, width: "100%"}) 
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
console.log(sum)
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
renderHabitCalendar(this.container, {year: 2023, month: 2, entries: data, filepath: dv.current().file.path, width: "100%"}) 
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
renderHabitCalendar(this.container, {year: 2023, month: 2, entries: data, filepath: dv.current().file.path, width: "100%"}) 
```