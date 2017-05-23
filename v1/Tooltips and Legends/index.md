# Tooltips and Legends

By default every chart that requires a Tooltip or Legend, initializes a new instance of
<a ng-href="/App/documentation/beta/{{sms.platfom}}/LiveCharts-Wpf-DefaultLegend">DefaultLegend</a>  or
<a ng-href="/App/documentation/beta/{{sms.platfom}}/LiveCharts-Wpf-DefaultTooltip">DefaultTooltip</a>.

### Customizing defaults

You can customize the background color, bullet size, or orientation, of these objects, as shown in the next block:

```{uwp||wpf}
&lt;lvc:CartesianChart Series="{Binding SeriesCollection}">
    &lt;lvc:CartesianChart.ChartLegend>
        &lt;lvc:DefaultLegend BulletSize="20" Background="Red"/>
    &lt;/lvc:CartesianChart.ChartLegend>
    &lt;lvc:CartesianChart.DataTooltip>
        &lt;lvc:DefaultTooltip BulletSize="20" Background="Gray"/>
    &lt;/lvc:CartesianChart.DataTooltip>
&lt;/lvc:CartesianChart>
```

```{wf}
cartesianChart1.Datatooltip.Bulletize = 20;
cartesianChart1.DataTooltip.Background = Brushes.Red;
```

You can also set the selection mode of your tooltip, for example with the next code we force our tooltip to display only the point that was hovered.

```{wpf||uwp}
&lt;lvc:CartesianChart Series="{Binding SeriesCollection}">
    &lt;lvc:CartesianChart.DataTooltip>
        &lt;lvc:DefaultTooltip SelectionMode="OnlySender" />
    &lt;/lvc:CartesianChart.DataTooltip>
&lt;/lvc:CartesianChart>
```

```{wf}
cartesianChart1.DataTooltip.SelectionMode = LiveCharts.TooltipSelectionMode.OnlySender;
```

An alternative sample:{uwp||wpf}

```{uwp||wpf}
&lt;lvc:CartesianChart>
        &lt;lvc:CartesianChart.Resources>
            &lt;Style TargetType="lvc:DefaultTooltip">
                &lt;Setter Property="Background" Value="DarkOrange">&lt;/Setter>
                &lt;Setter Property="Foreground" Value="White">&lt;/Setter>
                &lt;Setter Property="ShowTitle" Value="False">&lt;/Setter>&lt;!--new property-->
                &lt;Setter Property="ShowSeries" Value="False">&lt;/Setter>&lt;!--new property-->
                &lt;Setter Property="FontSize" Value="16">&lt;/Setter>
                &lt;Setter Property="FontWeight" Value="Bold">&lt;/Setter>
                &lt;Setter Property="CornerRadius" Value="20">&lt;/Setter>
                &lt;Setter Property="Width" Value="40">&lt;/Setter>
                &lt;Setter Property="Height" Value="40">&lt;/Setter>
                &lt;Setter Property="BorderThickness" Value="0">&lt;/Setter>
            &lt;/Style>
        &lt;/lvc:CartesianChart.Resources>
        &lt;lvc:CartesianChart.Series>
            &lt;lvc:LineSeries Values="4,2,6,4">&lt;/lvc:LineSeries>
        &lt;/lvc:CartesianChart.Series>
    &lt;/lvc:CartesianChart>
```

Would result in the following tooltip{wpf||uwp}

![{wpf||uwp}](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/customtooltip.gif)

### From Scratch

The previous block works when you need to customize the appearance of your chart components, but how about modifying the way the data is displayed in the tooltip, or showing extra properties in your tooltips?

Sadly there is not a native way to do this in WinForms, since LiveCharts.Winforms is actually a wrapper for LieCharts.Wpf you must create a Wpf UserControl to make this work, it is easy and you don't really need advanced knowledge about WPF to make it work.{wf}

The *DefaultTooltip* and *DefaultLegend* classes are designed to work for all cases, if you need a specialized component you can define your own, the logic is the next, you create a custom *UserControl*, LiveCharts will inject the data the user needs to see in the tooltip, and you need to handle how to display this data according to your needs, you can do everything you know about WPF to make it work.

In the next sample, we will configure our chart to plot *CustomerVm* class, and we will build a custom tooltip to show more properties about our customers.

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/Customizing%20Tooltips.jpg)

### Tooltip from scratch

<pulled />

Right click in your solution explorer, Add -> New Item -> Browse for Class, name the file CustomerVm.cs and replace the generated file content with:

```{!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/CustomTooltipAndLegend/CustomerVM.cs}

```

Now we are going to build our own DataTooltip, this tooltip will display all the *CustomerVm* properties, Right click in your solution explorer Add -> New Item -> Browse for *User Control (WPF)*, name the UserControl CustomersTooltip.

Replace CustomersTooltip.xaml with:

```{!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/CustomTooltipAndLegend/CustomersTooltip.xaml}

```

And the code behind of the user control (CustomersTooltip.xaml.cs)

```{!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/CustomTooltipAndLegend/CustomersTooltip.xaml.cs}

```

The important part there is that CustomersTooltip implements*IChartTooltip* this interface requires our *UserControl* to Implement *INotifyPropertyChanged* and a new property *Data* of type <a ng-href="/App/documentation/beta/{{sms-platform}}/LiveCharts-Wpf-TooltipData">TooltipData</a>, LiveCharts will inject all it knows about the current points to show in the tooltip, your job is to display this data as you require.

Notice we used the *DataContext* property of the *UserControl*, and binded the *Data.Points* property to our *ItemsControl* to display the current points as we need.

### Legend from scratch

Lets also create a simple custom Legend, with a custom style, add another user control and name it *CustomersLegend*, the logic is the same as the custom tooltip, you implement *IChartLegend* then you handle the injected data by LiveCharts

<pulled />

```{!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/CustomTooltipAndLegend/CustomersLegend.xaml}

```

```{!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/CustomTooltipAndLegend/CustomersLegend.xaml.cs}

```

Finally let's set this customs controls to our chart.

```{!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/CustomTooltipAndLegend/CustomTooltipAndLegendExample.xaml}

```

And the code behind

```{!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/CustomTooltipAndLegend/CustomTooltipAndLegendExample.xaml.cs}

```

