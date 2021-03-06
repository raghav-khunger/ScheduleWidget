<<<<<<< HEAD
ScheduleWidget handles recurring events for calendars. Let's say we want to create a 
recurring event for the Critical Mass Bicycle Ride, which happens in many major cities
on the last Friday of every month. 

Code Sample:

// using ScheduleWidget.Enums; 
// using ScheduleWidget.ScheduledEvents; 
var aEvent = new Event() 
{ 
    ID = 1, 
	Title = "Critical Mass Bicycle Ride", 
	FrequencyTypeOptions = FrequencyTypeEnum.Monthly, 
	MonthlyIntervalOptions = MonthlyIntervalEnum.Last, 
	DaysOfWeekOptions = DayOfWeekEnum.Fri
=======
ScheduleWidget handles recurring events for calendars.

ScheduleWidget is a .NET scheduling engine that handles recurring events for calendars. I was influenced by Martin Fowler's white paper "Recurring Events for Calendars" in which he describes the broad software architecture for a recurring events scheduling engine. But I did not find any implementation of his idea in the wild. So this led me to write it myself. It's pretty easy to use ScheduleWidget. Suppose you have an event that occurs every Monday and Wednesday. Here's the code:

var aEvent = new Event()
{
    ID = 1,
    Title = "Every Mon and Wed",
    FrequencyTypeOptions = FrequencyTypeEnum.Weekly,    
    DaysOfWeekOptions = DayOfWeekEnum.Mon | DayOfWeekEnum.Wed
>>>>>>> fe1521d35db1a846acfcfe665601556481a02500
};

var schedule = new Schedule(aEvent);

<<<<<<< HEAD
// give me all the upcoming dates for the next year
var range = new DateRange() 
{ 
    StartDateTime = DateTime.Now, 
	EndDateTime = DateTime.Now.AddYears(1) 
}; 

var occurrences = schedule.Occurrences(range);

foreach(var date in occurrences)
{
	System.Diagnostics.Debug.Print(date);
}

Download the ScheduleWidget Sample Project for a fully-functional test harness that
illustrates how best to use the ScheduleWidget engine. The project home page is at:
http://www.squarewidget.com/schedulewidget
=======
Now the schedule object can calculate the calendar dates for the event. Suppose I want to know if the event occurs today:

bool occursToday = schedule.IsOccurring(DateTime.Today);

Or maybe I want to get the dates for the next three months:

var range = new DateRange()
{    
    StartDateTime = DateTime.Today,
    EndDateTime = DateTime.Today.AddMonths(3)
};

IEnumerable<DateTime> dates = schedule.Occurrences(range);

You can model one-time, daily, weekly, bi-weekly, quarterly, monthly, and yearly (anniversary) intervals. You can make exceptions for holidays. It works great with FullCalendar or any other javascript-based calendar control. 
>>>>>>> fe1521d35db1a846acfcfe665601556481a02500
