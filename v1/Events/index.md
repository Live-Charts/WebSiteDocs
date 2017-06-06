# Events

The *CartesianChart* object exposes many events, any event has also a equivalent property of type *ICommand*. The next table shows the supported events, and when they are fired:

### Supported events

<table class="table table-striped">
<thead>
<tr>
<th>Name</th><th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Chart.UpdaterTick or Chart.UpdaterTickCommand</td>
<td>Fired every time The chart updates</td>
</tr>
<tr>
<td>Chart.DataClick or Chart.DataClickCommand</td>
<td>Occurs every time the users click over a point in a chart</td>
</tr>
<tr>
<td>Chart.DataHover or Chart.DataHoverCommand</td>
<td>Happens every time the users hovers over a point in a chart</td>
</tr>
<tr>
<td>Axis.RangeChanged or Axis.RangeChangedCommand</td>
<td>Occurs every time the range of an axis changes, including when a user uses features such as zooming and panning</td>
</tr>
</tbody>
</table>

### Sample

This section includes a pratical sample using events and commands.

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/eventsgif.gif)

<pulled></pulled>

### XAML{wpf||uwp}

```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/Events/EventsExample.xaml}

```

```{uwp,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Uwp/CartesianChart/Events/EventsExample.xaml}

```

### Code Behind

```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/Events/EventsExample.xaml.cs}

```

```{uwp,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Uwp/CartesianChart/Events/EventsExample.xaml.cs}

```

```{wf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/WinForms/Cartesian/Events/EventsExample.cs}

```

### XAML{uwp||wpf}

```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/WinForms/Cartesian/Events/EventsExample.cs}

```

```{uwp,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Uwp/CartesianChart/Events/EventsExample.xaml}

```

```{wf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/WinForms/Cartesian/Events/EventsExample.cs}

```

### ViewModel.cs{wpf||uwp}

```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/Events/ViewModel.cs}

```

```{uwp,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Uwp/CartesianChart/Events/ViewModel.cs}

```

### MyCommand.cs{wpf||uwp}

```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/Events/ChartPointCommandHandler.cs}

```

```{uwp,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Uwp/CartesianChart/Events/ChartPointCommandHandler.cs}

```
