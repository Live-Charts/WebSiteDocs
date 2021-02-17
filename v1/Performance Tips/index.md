﻿<h3 class="important-tittle">Improve Performance</h3>

<p>
    LiveCharts is not a drawing library, it is more like an algebra library, the process to render a chart
    is the next: the core of the library
    reads the size of the canvas in the view, WPF in this case, then according to the data
    in the chart it calculates the size and position of every label and shape required by each series,
    axis or legend in the chart, finally the core says to the view, hey! you need to draw a line here,
    and a rectangle here and please add a label here too.
</p>

<p>
    This way we have native controls according to each platform, once we are ready with
    WPF we can "easily" create the view for some other platform using its native drawing tools or if the
    platform is not good enough then use any other 3rd party component to render our charts.
</p>

<p>
    We can say that the library has 2 main processes,
    <b>Calculus</b> and <b>Rendering</b>, the first one is normally really fast, 
    sadly as any other WPF control, rendering has a poor performance when it is not used correctly.
</p>

<p>
    In general to improve performance you must:
</p>

<h3 class="spaced">Use the geared Package</h3>

<p>
    The geared package is a set of light weight series that connects with this library,
    it allows your charts to have million of points, and keep your UI responsive.
</p>

<p>
    It has a low price compared with any other charting library,
    and many of them do not offer a lot of features LiveCharts does, learn more about this package
    it will surely boost you application
</p>

<div class="text-center spaced">
    <a class="btn btn-lg btn-primary card-shadow" href="/licensing/pricing">
        Learn More
    </a>
</div>

<h3 class="spaced">Disable Animations</h3>

<p>
    You can easily turn off animations when you need a better performance
</p>

<pre class="prettyprint">&lt;lvc:CartesianChart DisableAnimations="True" /></pre>

<h3 class="spaced">Reduce the number shapes in your chart</h3>

<p>
    <b>a)</b> With version 1.x and lower, you must not enable <a class="text-muted">Series.DataLabels</a> when you
    have big data sets, because they are both, hard to read and heavy with the UI.
</p>

<p>
    <b>b)</b> Keep the number of <a href="/App/examples/v1/wpf/Events%20and%20Ui%20Elements">visual elements</a>,
    <a href="/App/examples/v1/wpf/Sections">sections</a> and
    <a href="/App/examples/v1/wpf/Multiple%20Axes">axes</a> lower than 25.
</p>

<p>
    <b>c)</b> When possible, disable hovering, use a null tooltip and remove any <i class="text-muted">DataClick</i>
    event from your chart, this is not necessary if you are using the Geared package.
</p>

<pre class="prettyprint">&lt;lvc:CatesianChart Hoverable="False" DataTooltip="{x:Null}" /></pre>

<h3 class="spaced">Freeze all you can</h3>

<p>
    When you are sure your strokes, fills or PointGeometies are not going to change then freeze them.
    By default since 0.7.15 version, default strokes, fills and geometries are frozen, you can find
    more information about it <a href="https://msdn.microsoft.com/en-us/library/ms750509(v=vs.110).aspx">here</a>
</p>

<h3 class="spaced">Avoid calling <i class="text-muted">.Add()</i> multiple times</h3>

<p>
    When adding a range of values to your chart, then please use the <i class="text-muted">.AddRange()</i>
    method, it is not a good practice to call the <i class="text-muted">.Add()</i> method multiple times 
    in a short period of time
</p>

<b>Do Not</b>

<pre class="prettyprint">var cv = new ChartValues&lt;double>();

for (var i = 0; i &lt; 1000; i++){
    cv.Add(5);
}</pre>

<b>Instead Do</b>

<pre class="prettyprint">var temporalCv = new double[1000];

for (var i = 0; i &lt; 1000; i++){
    temporalCv[i] = 5;
}

var cv = new ChartValues&lt;double>();
cv.AddRange(temporalCv);

//or you can also
var cv = temporalCv.AsGearedValues();
</pre>
