## Obsidian Habit Tracker Dataview Plugin

This plugin creates a calendar, showing your habit status within a month. It's based on the [Habit Track](https://github.com/duoani/obsidian-habit-tracker) plugin by [@duoani](https://github.com/duoani).


## How To

This plugin is intended to be used alongside [DataviewJS](https://blacksmithgu.github.io/obsidian-dataview/). All you need to do is prepare the data and call `renderHabitCalendar` in a dataviewjs code block.

~~~
```dataviewjs
renderHabitCalendar(this.container, {year: 2023, month: 1, entries: [{date: '2023-01-01',  content: '⭐'}]}) 
```
~~~

The first argument should be the html container in which the calendar will be created.

You can pass the habit data and styles thru the second argument. The following fields are supported:

- `year`: year of the calendar, apparently
- `month`: month of the calendar
- `entries`: a list of entries containing the habit data per day. A entry contains
    - `date`: date of the habit
    - `content`: whatever you want to put in the calendar
- `format`: the way you want `entries[i].content` to be rendered. Choose `html` or `markdown` to render as html or markdown, make sure their cooresopnding settings are enabled in the settings tab. Leave empty to treat the content as plain text.
- `filepath`: if you want to render the content as markdown, pass the current file path thru this field.


## Plans

- [x] jump right to the diary on click
- [x] preview diary on hovering
- [x] support render markdown in calendar