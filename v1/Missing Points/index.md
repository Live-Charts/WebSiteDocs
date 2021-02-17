﻿<h3 class="important-tittle">Line with missing points</h3>

<p>
    Use <i>double.NaN</i> when you don't know a value in a line series, that point will be undefined and
    will be ignored when the series is drawn.
</p>

<div class="text-center">
    <img src="/App/Examples/v1/Missing Points/Images/interrupted.jpg" />
</div>

<div class="doc-alert">
    To keep this example always up to date it is directly pulled from the Github repository, the
    repo for simplicity uses the <i>UserControl</i> class to wrap every example, but you can use any
    container for your plots.
</div>


```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/Missing%20Line%20Points/MissingPointsExample.xaml.cs}

```

```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/Missing%20Line%20Points/MissingPointsExample.xaml}

```


```{wf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/WinForms/Cartesian/MissingPoints/MissingPoint.cs}

```
