﻿<h3 class="important-tittle">Zooming and panning</h3>

<p>
    Use <i class="text-muted">Chart.Zoom (default is None)</i> and <i class="text-muted">Chart.Pan (default is Unset)</i>,
    use the mouse wheel to zoom in/out, click, hold and drag for panning.
</p>

<p>
    Notice in this case we are plotting an already configured type in LiveCharts <i>(DatetimePoint)</i>, 
    you can use this type or <a href="/App/examples/v1/wpf/Types%20and%20Configuration">configure</a> your own.
</p>

<p>
    You can easily zoom or pan grammatically only setting the axis limits, for more information see the
    <a href="/App/examples/v1/wpf/Data%20Pagination">Data Pagination</a> article
</p>

<div class="text-center">
    <img src="/App/Examples/v1/Zooming and panning/Images/zandp.gif"/>
</div>

<div class="doc-alert">
    To keep this example always up to date it is directly pulled from the Github repository, the
    repo for simplicity uses the <i>UserControl</i> class to wrap every example, but you can use any
    container for your plots.
</div>

```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/ZoomingAndPanning/ZoomingAndPanning.xaml.cs}

```

```{wpf,!"https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/ZoomingAndPanning/ZoomingAndPanning.xaml}

```

```{wf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/WinForms/Cartesian/Zooming%20and%20Panning/ZomingAndPanningExample.cs}

```
