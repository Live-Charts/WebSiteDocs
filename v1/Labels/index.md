# Labels

A Label is any string representation of any value in the chart, they are normally placed over the axis length and in tool tips.

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/labels.jpg)

### Axis Labels

An *Axis* has 2 types of labels, formatted and mapped labels.

### Formatted Labels

A formatted label is shown at the top of this article at the Y axis, a Formatted label is useful when there is a direct conversion between the chart value and the label, 
for example, in the image above, the Y axis has a range of values between 8 and 26, but because of  the current formatter, we are able to see '8' as '8.00k items'.

To achieve this use the *Axis.LabelFormatter* property, it stores a function that takes a double 
value as parameter and returns a string, LiveCharts will use this function every time it needs to display a chart value as *string*.

```
MyAxis.LabelFormatter = val => val.ToString("C"); //as currency
MyAxis.LabelFormatter = val => val + "°"; //as degrees
MyAxis.LabelFormatter = val => val + ".00 items sold"; //or any other custom format
```

### Mapped Labels

A mapped label is shown at the top of this article at the X axis, they are normally useful to map a position with a name, for example when the first 
point belongs to John, the second to Susan and the third one to Charles.

```{wpf}
&lt;lvc:BarChart&gt;
  &lt;lvc:BarChart.AxisX&gt;
    &lt;lvc:Axis Title="Month" Labels="John, Susan, Charles" /&gt;
  &lt;/lvc:BarChart.AxisX&gt;
&lt;/lvc:BarChart&gt;
```

```{uwp}
//Code Behind
Labels = new string[] {"John", "Charles", "Susan"};

//XAML
&lt;lvc:BarChart&gt;
  &lt;lvc:BarChart.AxisX&gt;
    &lt;lvc:Axis Title="Month" Labels="{Binding Labels}" /&gt;
  &lt;/lvc:BarChart.AxisX&gt;
&lt;/lvc:BarChart&gt;
```

```{wf}
cartesianChart1.AxisX.Add(new LiveCharts.Wpf.Axis
{
   Labels = new string[] {"John", "Charles", "Susan"}
})
```

Labels are mapped according to the position (zero-indexed) of each label in our labels collection,  when a chart requires to draw a label for *X = 0*, it will pull *Labels[0]*, when *X = 1* the label will be *Labels[1]* .... when *X = n* => *Labels[n]*.

Notice that if the axis value is greater than <i>Labels.Count</i> an empty string will be returned.

*Axis.Labels* hides *Axis.LabelFormatter*, therefore if *Axis.Labels* is not null then labels will be pulled from *Axis.Labels*, if *Axis.Labels* is null then LiveCharts will use the formatter, if both are null then the raw value will be used as label.

### Data Labels

Any time you need a label on every point of your series (<small class="text-muted">as shown in image</small>), set the *Series.DataLabels* property to *true*.

if necessary, you can also customize the DataLabel format using the *Series.LabelPoint* property

```
new ColumnSeries
{
   Values = new ChartValues&lt;double> { 4, 2, 8, 2, 3, 0, 1 },
   DataLabels = true,
   LabelPoint = point => point.Y + "K"
}
```

### Rotating labels

Some times your labels are long, and you need to optimize the space, in this case you can rotate any axis labels, You can use any angle, even negatives.

```{wpf||uwp}
&lt;lvc:CartesianChart Grid.Row="2" Series="{Binding SeriesCollection}"&gt;
  &lt;lvc:CartesianChart.AxisX&gt;
    &lt;lvc:Axis LabelsRotation="13" Labels="{Binding Labels}"&gt;
      &lt;lvc:Axis.Separator&gt;
        &lt;!--
        force the separator step to 1, so it always display all labels
        if you don't force the separator, it will be calculated 
        automatically, and could skip some labels,
        disable it to make it invisible
        -->
        &lt;lvc:Separator IsEnabled="False" Step="1"&gt;
          &lt;/lvc:Separator&gt;
        &lt;/lvc:Axis.Separator&gt;
      &lt;/lvc:Axis&gt;
    &lt;/lvc:CartesianChart.AxisX&gt;
  &lt;lvc:CartesianChart.AxisY&gt;
&lt;/lvc:CartesianChart&gt;
```

```{wf}
cartesianChart1.AxisX.Add(new LiveCharts.Wpf.Axis
{
   Labels = new[]
   {
      "Shea Ferriera",
      "Maurita Powel",
      "Scottie Brogdon"
   },
   LabelsRotation = 13,
   Separator = new Separator // force the separator step to 1, so it always display all labels
   {
     Step = 1, // if you don't force the separator, it will be calculated automatically, and could skip some labels
     IsEnabled = false //disable it to make it invisible.
   }
});
```

### Sample

<pulled ></pulled>

The image in the top of this article is the result of:

### Code Behind

```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/Labels/LabelsExample.xaml.cs}

```

```{uwp,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Uwp/CartesianChart/Labels/LabelsExample.xaml.cs}

```

```{wf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/WinForms/Cartesian/Labels/Labels.cs}

```

### XAML{wpf||uwp}

```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/Labels/LabelsExample.xaml}

```

```{uwp,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Uwp/CartesianChart/Labels/LabelsExample.xaml}

```