﻿<h3 class="important-tittle">Scrollable Chart</h3>

<div class="text-center">
    <img src="https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Scrollable/Images/scrollable.gif" />
</div>

<uses-geared></uses-geared>

<div class="doc-alert">
    This article might not work properly in version 0.9.3 or lower
</div>

<div class="doc-alert">
    To keep this example always up to date it is directly pulled from the Github repository, the
    repo for simplicity uses the <i>MetroWindow</i> class, from <a href="http://mahapps.com/">Mahapps</a> to wrap this example, but you can use any
    container for your plots.
</div>

<p>
    Drag 2 charts from your toolbox, name one cartesianChart1 and the second one scrollerChart, we'll use the second chart as a scrolling bar.
</p>

```{wf,!https://raw.githubusercontent.com/Live-Charts/GearedExamples/master/WinForms/ScrollableChart/ScrollableViewModel.cs}

```

```{wf,!https://raw.githubusercontent.com/Live-Charts/GearedExamples/master/WinForms/ScrollableChart/ScrollableExample.cs}

```

```{wpf,!https://raw.githubusercontent.com/Live-Charts/GearedExamples/master/Wpf/Scrollable/ScrollableView.xaml}

```

```{wpf,!https://raw.githubusercontent.com/Live-Charts/GearedExamples/master/Wpf/Scrollable/ScrollableView.xaml.cs}

```


