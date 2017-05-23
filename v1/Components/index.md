# Components

LiveCharts is designed to be easy for the user, everything is updated and animated
automatically, the library will only update when it considers it is necessary, not every time 
your data changes, when you add/remove series, or add/remove values the chart will update by itself,
you really don’t need to worry about anything but your business, let LiveCharts handle the charting.

### Starting Sample

There are many types ready to plot already defined, you can learn more in the
[Types and Configuration section](/App/examples/v1/{{sms.platform}}/Types%20and%20Configuration), in 
this brief example we are plotting double values.

*Code Behind*

```{wpf||uwp}
SeriesCollection = new SeriesCollection
{
    new LineSeries
    {
        Values = new ChartValues&lt;double> { 3, 5, 7, 4 }
    },
    new ColumnSeries                
    {
        Values = new ChartValues&lt;decimal> { 5, 6, 2, 7 }
    }
};
```
```{wf}
myChart.Series = new SeriesCollection
{
    new LineSeries
    {
        Values = new ChartValues&lt;double> { 3, 5, 7, 4 }
    },
    new BarSeries                
    {
        Values = new ChartValues&lt;decimal> { 5, 6, 2, 7 }
    }
};
```

*XAML{wpf||uwp}*

```{wpf||uwp}
&lt;lvc:CartesianChart Series="{Binding SeriesCollection}" />
```

Simple isn't it? that is all you need, now every time you add/remove a series to the SeriesCollection 
instance or add/remove a value at every series, the chart will update and animate automatically.

### Components

The next image will guide you to get more familiar with LiveCharts components.

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/components.png)

All the series have *Stroke* and *Fill* properties.

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/strokeandfill.png)

You can set a Fill and Stroke only for a specific series, if you don't then the library will decide a 
color according to your [theme](/App/examples/v1/{{sms.platform}}/Themes") and the series positions in 
the *Chart.SeriesCollection* property, colors will repeat if necessary.{wpf||uwp}

You can set a Fill and Stroke only for a specific series, if you don't then the library will decide a 
color according to the series positions in the *Chart.SeriesCollection* property, colors will
repeat if necessary.{wf}

```{wpf||uwp}
&lt;lvc:LineSeries Stroke="Red" Fill="Blue /"&gt;
```

```{wf}
//use the Stroke/Fill for a specific series
mySeries.Stroke = System.Windows.Media.Brushes.Red;
mySeries.Fill = System.Windows.Media.Brushes.Blue;

//change the base colors array:
LiveCharts.Wpf.Charts.Chart.Base.Colors = new List&lt;System.Windows.Media.Color&gt;
{
  System.Windows.Media.Colors.Red,
  System.Windows.Media.Colors.Blue,
  System.Windows.Media.Colors.Green
};
```

### Properties

Setting the *Series.Visibility* (will define the drawn shape visibility), 
*Panel.ZIndex* (drawn shape z-index property), *Series.StrokeDashArray* (dashed strokes) properties
will be binded to the drawn shape, for example:

```{wpf}
&lt;lvc:LineSeries Visibility="Hidden" StrokeDashArray="2" Panel.Zindex="3" / &gt;
```

```{uwp}
&lt;lvc:LineSeries Visibility="Hidden" StrokeDashArray="2" Canvas.Zindex="3" / &gt;
```

```{wf}
mySeries.Visibility = System.Windows.Visibility.Hidden;
mySeries.StrokeDashArray = new System.Windows.Media.DoubleCollection {2};
System.Windows.Controls.Panel.SetZIndex(mySeries, 3);
```

### Custom Components

If necessary you can also define your own tooltips or legends controls,
[here](/App/examples/v1/{{sms.platform}}/Customizing%20Tooltips) is an article about it.


### Legend

You can place a legend at Bottom, Top, Right or Left, just set the *Chart.LegendPosition* property 
at the desired location.

```
myChart.LegendLocation = LegendLocation.Right;
```