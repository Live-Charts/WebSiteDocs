﻿<h3 class="important-tittle">Date Time</h3>

<p>
    To handle date time in LiveCharts you must create a custom scale for your charts, it is not hard but please
    before reading this article identify if this is necessary, if you need just simple labels as 
    "January, February, March", and all of them are separated by a regular interval then maybe just using
    <a href="/App/examples/v1/wpf/Labels">Axis.Labels</a> is enough, understanding how LiveCharts 
    <a href="/App/examples/v1/wpf/Types%20and%20Configuration">works</a> is also helpful.
</p>

<div class="text-center">
    <img src="/App/Examples/v1/Date Time/Images/datetime.jpg"/>
</div>

<h4>XAML</h4>

<pre class="prettyprint">&lt;lvc:CartesianChart Series="{Binding Series}"&gt;
  &lt;lvc:CartesianChart.AxisX&gt;
    &lt;lvc:Axis LabelFormatter="{Binding Formatter}"&gt;&lt;/lvc:Axis&gt;
  &lt;/lvc:CartesianChart.AxisX&gt;
&lt;/lvc:CartesianChart&gt;</pre>

<h4>Code Behind</h4>

<p>
    In this case we are going to plot a custom type defined in the next code snippet
</p>

<pre class="prettyprint" url="https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/Using%20DateTime/DateModel.cs"></pre>

<div class="doc-alert">
    <b>Note</b> to keep this example always up to date it is directly pulled from the Github repository, the
    repo for simplicity uses <i>UserControl</i> class to wrap every example, but you do
    not need to wrap you chart with a <i>UserControl</i>, you can add it directly in any
    <i>Window</i> or any other Wpf Element
</div>

<pre class="prettyprint" url="https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/Using%20DateTime/DateTime.xaml.cs"></pre>

<h4>XAML</h4>

<pre class="prettyprint" url="https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/Using%20DateTime/DateTime.xaml"></pre>

<h4>The Bars Problem</h4>

<p>
    For now everything is simple, just one problem with this method, when you need any bar series, the bar's
    width is unitary (1), notice we are using DateTime.Ticks as X, so the width of the bar is 1 tick
    and 1 tick is 1 millisecond, notice our points are separated by 2 hours, the bar series is being drawn
    but with a width of 1 millisecond, 1 millisecond is invisible in an interval of 2 hours,
    so how do we make our bars visible?
</p>

<p>
    We need to change the unit of the chart, in this case we are going to use hours
</p>

<pre class="prettyprint">var dayConfig = Mappers.Xy&lt;DateModel&gt;()
  .X(dateModel => dateModel.DateTime.Ticks/TimeSpan.FromHours(1).Ticks)
  .Y(dateModel => dateModel.Value);
//and the formatter
Formatter = value => new DateTime((long) (value*TimeSpan.FromHours(1).Ticks)).ToString("t");
</pre>

<p>
    Now instead the unit of the chart is one hour, and the bars width will be 1 hour.
</p>

<p>
    The next set of examples show how to configure your chart's scale in many time intervals
</p>

<pre class="prettyprint">
//Every 15 minutes
var dayConfig = Mappers.Xy&lt;DateModel&gt;()
  .X(dateModel => dateModel.DateTime.Ticks/TimeSpan.FromMinutes(15).Ticks)
  .Y(dateModel => dateModel.Value);
//and the formatter
Formatter = value => new DateTime((long) (value*TimeSpan.FromMinutes(15).Ticks)).ToString("t");

//Days
var dayConfig = Mappers.Xy&lt;DateModel&gt;()
  .X(dateModel => dateModel.DateTime.Ticks/TimeSpan.FromDays(1).Ticks)
  .Y(dateModel => dateModel.Value);
//and the formatter
Formatter = value => new DateTime((long) (value*TimeSpan.FromDays(1).Ticks)).ToString("d");

//Months
//30.44 is the average days in a solar year
var dayConfig = Mappers.Xy&lt;DateModel&gt;()
  .X(dateModel => dateModel.DateTime.Ticks/(TimeSpan.FromDays(1).Ticks*30.44))
  .Y(dateModel => dateModel.Value);
//and the formatter
Formatter = value => new DateTime((long) (value*TimeSpan.FromDays(1).Ticks*30.44)).ToString("M");

//Years
//365.2425 is the days in a solar year
var dayConfig = Mappers.Xy&lt;DateModel&gt;()
  .X(dateModel => dateModel.DateTime.Ticks/(TimeSpan.FromDays(1).Ticks*365.2425))
  .Y(dateModel => dateModel.Value);
//and the formatter
Formatter = value => new DateTime((long) (value*TimeSpan.FromDays(1).Ticks*365.2425)).ToString("yyyy");</pre>

<p>
    <b>Note:</b> because not all the months and years have the same number of days, the width of every bar could vary
    for months: +-(1/30.44) and for years: +-(1/365.2425), a small and depreciable visual error.
</p>
