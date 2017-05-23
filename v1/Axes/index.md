### Axes

You can practically custom everything in LiveCharts and axes are not the exception, the next image illustrates an axis:

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/axis%20explain.jpg)

### Title

Use the _Title_ property to add a label an axis.

```
myAxis.Title = "Population"
```

### Separators

You can find an illustrator of a separator at the top of this article, you can specify the distance between each separator using the _Axis.Separator.Step_ property, when this property is equals to _double.NaN_ the library will calculate the distance automatically based on your charts size and the range of values in your current _Axis_.

When the _Axis.Separator.IsEnabled_ property is equals to _false_, then LiveCharts will not draw the separator, notice that disabling the separator is not enough to hide the labels of an axis, you can use the _Axis.ShowLabels_ property to specify whether an axis should draw its labels.

```{wpf||uwp}
<lvc:CartesianChart Series="{Binding SeriesCollection}">
  <lvc:CartesianChart.AxisX>
    <lvc:Axis ShowLabels="false">
      <lvc:Axis.Separator>
        <lvc:Separator IsEnabled="False" Step="1" />
        </lvc:Axis.Separator>
      </lvc:Axis>
    </lvc:CartesianChart.AxisX>
  <lvc:CartesianChart.AxisY>
</lvc:CartesianChart>
```

```{wf}
cartesianChart1.AxisX.Add(new LiveCharts.Wpf.Axis
{
   Separator = new Separator 
   {
     Step = 1,
     IsEnabled = false
   }
});
```

**Warning!** Be careful when forcing steps, it could result in performance issues, if not used correctly, if your current range of values goes from 0 to 1,000 and you set the step to 1, the chart will draw 1,000 separators too.

In the next block, we are forcing our separator's step to 30 seconds:

```{wpf||uwp}
//Code Behind
Step = TimeSpan.FromSeconds(30).Ticks;

//XAML
<lvc:CartesianChart Series="{Binding SeriesCollection}">
    <lvc:CartesianChart.AxisX>
        <lvc:Axis Labels="{Binding Labels}">
            <lvc:Axis.Separator>
               <lvc:Separator IsEnabled="False" Step="{Binding Step}"></lvc:Separator>
            </lvc:Axis.Separator>
        </lvc:Axis>
    </lvc:CartesianChart.AxisX>
    <lvc:CartesianChart.AxisY>
       <lvc:Axis Title="Sold Items" LabelFormatter="{Binding Formatter}"></lvc:Axis>
    </lvc:CartesianChart.AxisY>
</lvc:CartesianChart>
```

```{wf}
new Axis
{
    Separator = new Separator
    {
        Step = TimeSpan.FromSeconds(30).Ticks,
        IsEnabled = false
    }
}
```

### Styling Separators

Notice setting _Axis.Separator.IsEnabled_ property to false will make the separator invisible.

```{uwp||wpf}
<lvc:CartesianChart Background="#222E31">
  <lvc:CartesianChart.Series>
    <lvc:LineSeries Values="{Binding Values1}" />
    <lvc:LineSeries Values="{Binding Values2}" />
  </lvc:CartesianChart.Series>
  <lvc:CartesianChart.AxisX>
    <lvc:Axis IsMerged="True">
      <lvc:Axis.Separator>
        <lvc:Separator StrokeThickness="1" StrokeDashArray="2">
          <lvc:Separator.Stroke>
            <SolidColorBrush Color="#404F56" />
          </lvc:Separator.Stroke>
        </lvc:Separator>
      </lvc:Axis.Separator>
    </lvc:Axis>
  </lvc:CartesianChart.AxisX>
  <lvc:CartesianChart.AxisY>
    <lvc:Axis IsMerged="True">
      <lvc:Axis.Separator>
        <lvc:Separator StrokeThickness="1.5" StrokeDashArray="4">
          <lvc:Separator.Stroke>
            <SolidColorBrush Color="#404F56" />
          </lvc:Separator.Stroke>
        </lvc:Separator>
      </lvc:Axis.Separator>
    </lvc:Axis>
  </lvc:CartesianChart.AxisY>
</lvc:CartesianChart>
```

```{wf}
cartesianChart1.AxisX.Add(new Axis
{
   IsMerged = true,
   Separator = new Separator
   {
      StrokeThickness = 1,
      StrokeDashArray = new System.Windows.Media.DoubleCollection(new double[] { 2 }),
      Stroke = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(64, 79, 86))
   }
});

cartesianChart1.AxisY.Add(new Axis
{
   IsMerged = true,
   Separator = new Separator
   {
      StrokeThickness = 1.5,
      StrokeDashArray = new System.Windows.Media.DoubleCollection(new double[] { 4 }),
      Stroke = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(64, 79, 86))
   }
});
```

### Merged Axes

When you need to save some space, merge any axis in the chart, try using the _Axis.IsMerged_ property to true, the next image shows a merged axis (left) vs a normal axis (right)

### Axes positioning

No matter if you have 1 or 10 axes, you could always specify where the axis is stacked, using the _Axis.Position_ property, options are _RightTop, LeftBottom_.

```{wpf||uwp}
<lvc:Axis Position="RightTop" />
```

```{wf}
new Axis { Position = Position = AxisPosition.LeftBottom }
```