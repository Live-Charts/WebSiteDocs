  
﻿<h4 class="important-tittle">Multiple axes</h4>

<p>
    You can add as many axes as you need, every axes scales independently with its
    own series, to add a series to an axis you must specify it using the
    <i>Series.ScalesXAt</i> or <i>Series.ScalesYAt</i> the default value of both
    properties is zero.
</p>

<div class="text-center">
    <img src="/App/Examples/v1/Multiple Axes/Images/multiax.jpg"/>
</div>

<div class="doc-alert">
    To keep this example always up to date it is directly pulled from the Github repository, the
    repo for simplicity uses the <i>UserControl</i> class to wrap every example, but you can use any
    container for your plots.
</div>

```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/MultiAxes/MultiAxesChart.xam;l}

```

```{wf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/WinForms/Cartesian/MultiAxes/MultipleAxesExample.cs}

```
