---
title: home
layout: home
---
<html lang="en">
<link rel="stylesheet" href="https://codepen.io/utbaz/pen/MWGygLe?editors=0100.css">
<body>
		<div class="cal__main">
			<span class="background"></span>
			<span class="background1"></span>
			<span class="background2"></span>
			<h1>glassalendar</h1>
            <p>by Utba Zafar</p>
			<div class="cal__container">
				<div class="calendar__top">
					<span class="arrow" id="back__arrow"><</span>
					<div class="calendar__day">
						<span class="cal__month" id="cal__month"></span>
						<span class="cal__date" id="cal__date"></span>
					</div>
					<div class="calendar__time">
						<span class="cal__time" id="cal__time"></span>
					</div>
					<span class="arrow" id="next__arrow">></span>
				</div>
				<div class="calendar__bottom">
					<div class="cal__weekdays" id="cal__weekdays">
				</div>
					<div class="cal__days" id="cal__days"></div>
				</div>
			</div>
		</div>
        <script>
            const newMonth = document.getElementById('cal__month');
const dateDisplay = document.getElementById('cal__date');
const allDates = document.getElementById('cal__days');
const prevBtn = document.getElementById('back__arrow');
const nxtBtn = document.getElementById('next__arrow');
const timeDisplay = document.getElementById('cal__time');

const date = new Date();

// Current Date Display
currentDate = () => {
	const twelveMonths = [
		'January',
		'February',
		'March',
		'April',
		'May',
		'June',
		'July',
		'August',
		'September',
		'October',
		'November',
		'December',
	];

	const sevenDays = [
		'Sunday',
		'Monday',
		'Tuesday',
		'Wednesday',
		'Thursday',
		'Friday',
		'Saturday',
	];
	const date__weekDay = sevenDays[date.getDay()];
	const date__day = date.getDate();
	const date__year = date.getFullYear();

	newMonth.innerHTML = twelveMonths[date.getMonth()];
	dateDisplay.innerHTML = `${date__weekDay} ${date__day}, ${date__year}`;
};
currentDate();
        </script>
	</body>
</html>