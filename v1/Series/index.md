# Series

### Strokes and Fills

All the series have *Stroke* and *Fill* properties, these properties handle the color, both properties
type is *System.Windows.Media.Brush* you can use complex fills or stokes,
[here](https://msdn.microsoft.com/en-us/library/aa970904%28v=vs.100%29.aspx) is a good article about it.

```
mySeries.Fill = Brushes.Red;
mySeries.Stroke = Brushes.Blue;
```

### StrokeThickness and StrokeDashedArray

Use the *Series.StrokeThickness* property as you need, to draw dashed strokes you can use the
*Series.StrokeDashArray* property, you can find more information about dashed arrays
[here](http://searchwindevelopment.techtarget.com/tip/Understanding-line-stroke-patterns).

```
//XAML
&lt;lvc:LineSeries StrokeDashArray="2" /&gt;

//Code Behind
mySeries.StrokeDashArray = new DoubleCollection {2};
mySeries.StrokeThickness = 3;
```

### ZIndex

Every shape drawn by any series class is binded to the 
**Panel.ZIndex{wpf||wf}**
**Canvas.ZIndex{uwp}**
property, you can control which series is over or under in the z plane, here is a short sample:

```{wpf}
&lt;lvc:LineSeries Panel.ZIndex="0" /&gt;
&lt;lvc:LineSeries Panel.ZIndex="1" /&gt;
&lt;lvc:LineSeries Panel.ZIndex="2" /&gt;
```

```{uwp}
&lt;lvc:LineSeries Canvas.ZIndex="0" /&gt;
&lt;lvc:LineSeries Canvas.ZIndex="1" /&gt;
&lt;lvc:LineSeries Canvas.ZIndex="2" /&gt;
```

```{wf}
System.Windows.Controls.Panel.SetZIndex(mySeries, 0);
System.Windows.Controls.Panel.SetZIndex(mySeries, 1);
System.Windows.Controls.Panel.SetZIndex(mySeries, 2)
```

### Visibility

All the drawn shapes are also binded to the *Series.Visibility* property, this allows us to control
series visibility at run time.

Notice any stacked series (including pie series) will not only change based on the *Visibility* property,
it will also remove the series from the stacked values, and the chart will be updated as if that series 
had not existed.

### Specialized properties

There are some properties that do only exist at certain series, to find more info about how to customize
every series, please browse the object explorer in this web site, for example browse 
[the line series object](/App/documentation/beta/{{sms.platform}}/LiveCharts-Wpf-LineSeries).


### A short sample

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/custom-line.jpg)

#### Code Behind{wpf||uwp}

```{wpf||uwp}
using LiveCharts;

namespace CartesianChart.Customized
{
    public partial class CustomizedExample 
    {
        public CustomizedExample()
        {
            InitializeComponent();

            Values1 = new ChartValues&lt;double&gt; { 3, 4, 6, 3, 2, 6 };
            Values2 = new ChartValues&lt;double&gt; { 5, 3, 5, 7, 3, 9 };

            DataContext = this;
        }

        public ChartValues&lt;double&gt; Values1 { get; set; }
        public ChartValues&lt;double&gt; Values2 { get; set; }

    }
}
```

```{wf}
using System;
using System.Drawing;
using System.Windows.Forms;
using LiveCharts;
using LiveCharts.Wpf;

namespace Winforms.Cartesian.Customized_Series
{
    public partial class CustomizedSeries : Form
    {
        public CustomizedSeries()
        {
            InitializeComponent();

            cartesianChart1.Series.Add(new LineSeries
            {
                Values = new ChartValues&lt;double> { 3, 4, 6, 3, 2, 6 },
                StrokeThickness = 4,
                StrokeDashArray = new System.Windows.Media.DoubleCollection(20),
                Stroke = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(107, 185, 69)),
                Fill = System.Windows.Media.Brushes.Transparent,
                LineSmoothness = 0,
                PointGeometry = null
            });
            cartesianChart1.Series.Add(new LineSeries
            {
                Values = new ChartValues&lt;double> { 5, 3, 5, 7, 3, 9 },
                StrokeThickness = 2,
                Stroke = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(28, 142, 196)),
                Fill = System.Windows.Media.Brushes.Transparent,
                LineSmoothness = 1,
                PointGeometrySize = 15,
                PointForeround =
                    new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(34, 46, 49))
            });

            cartesianChart1.Background = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(34, 46, 49));

            cartesianChart1.AxisX.Add(new Axis
            {
                IsMerged = true,
                Separator = new Separator
                {
                    StrokeThickness = 1,
                    StrokeDashArray = new System.Windows.Media.DoubleCollection(2),
                    Stroke = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(64, 79, 86))
                }
            });
            cartesianChart1.AxisY.Add(new Axis
            {
                IsMerged = true,
                Separator = new Separator
                {
                    StrokeThickness = 1.5,
                    StrokeDashArray = new System.Windows.Media.DoubleCollection(4),
                    Stroke = new System.Windows.Media.SolidColorBrush(System.Windows.Media.Color.FromRgb(64, 79, 86))
                }
            });

        }
    }
}
```

#### XAML{wpf||uwp}

```{wpf||uwp}
&lt;lvc:CartesianChart Background="#222E31"&gt;
  &lt;lvc:CartesianChart.Series&gt;
    &lt;lvc:LineSeries Values="{Binding Values1}" StrokeThickness="4" StrokeDashArray="2" 
                       Stroke="#6BBA45" Fill="Transparent" LineSmoothness="0" PointGeometry="{x:Null}" /&gt;
    &lt;lvc:LineSeries Values="{Binding Values2}" StrokeThickness="2" 
                       Stroke="#1C8FC5" Fill="Transparent" LineSmoothness="1" 
                       PointGeometrySize="15" PointForeround="#222E31"/&gt;
  &lt;/lvc:CartesianChart.Series&gt;
  &lt;lvc:CartesianChart.AxisX&gt;
    &lt;lvc:Axis IsMerged="True"&gt;
      &lt;lvc:Axis.Separator&gt;
        &lt;lvc:Separator StrokeThickness="1" StrokeDashArray="2"&gt;
          &lt;lvc:Separator.Stroke&gt;
            &lt;SolidColorBrush Color="#404F56" /&gt;
          &lt;/lvc:Separator.Stroke&gt;
        &lt;/lvc:Separator&gt;
      &lt;/lvc:Axis.Separator&gt;
    &lt;/lvc:Axis&gt;
  &lt;/lvc:CartesianChart.AxisX&gt;
  &lt;lvc:CartesianChart.AxisY&gt;
    &lt;lvc:Axis IsMerged="True"&gt;
      &lt;lvc:Axis.Separator&gt;
        &lt;lvc:Separator StrokeThickness="1.5" StrokeDashArray="4"&gt;
          &lt;lvc:Separator.Stroke&gt;
            &lt;SolidColorBrush Color="#404F56" /&gt;
          &lt;/lvc:Separator.Stroke&gt;
        &lt;/lvc:Separator&gt;
      &lt;/lvc:Axis.Separator&gt;
    &lt;/lvc:Axis&gt;
  &lt;/lvc:CartesianChart.AxisY&gt;
&lt;/lvc:CartesianChart&gt;
```