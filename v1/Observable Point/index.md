<h3 class="important-tittle">Observable Point</h3>

<p>
    All the charts by default update and animate when you add/remove series or values, but what happens when you
    need to update the chart every time a value changes? in this case you must implement the
    <i class="text-muted">IObservableChartPoint</i>, this enables a value to notify the chart
    to update every time it changes, this library already contains many
    <a href="/App/examples/v1/wpf/Types%20and%20Configuration">types</a> that do this by default.
</p>

<p>
    It is easy to implement and follows the MV* patterns.
</p>

<pre class="prettyprint">public class ObservableValue : IObservableChartPoint
{
    private double _value;        

    public event Action PointChanged;

    public double Value
    {
       get { return _value; }
       set
       {
            _value = value;
            OnPointChanged();
        }
    }

    protected void OnPointChanged()
    {
        if (PointChanged != null) PointChanged.Invoke();
    }
}</pre>

<p>
    The previous code shows the important parts in the already configured
    <i class="text-muted">ObservableValue</i> class, this class is able to notify the chart to
    update every time the <i class="text-muted">Value</i> property changes.
</p>

<p>
    Notice it is not necessary to configure <i class="text-muted">ObservableValue</i> class, since
    it is already loaded in the library, if you are using a custom type you must also let LiveCharts
    know <a href="/App/examples/v1/wpf/Types%20and%20Configuration">how to plot your type</a>
</p>

<div class="text-center">
    <img src="/App/Examples/v1/Observable Point/Images/fullyresponsive.gif" />
</div>

<div class="doc-alert">
    To keep this example always up to date it is directly pulled from the Github repository, the
    repo for simplicity uses the <i>UserControl</i> class to wrap every example, but you can use any
    container for your plots.
</div>

```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/MultiAxes/MultiAxesChart.xaml}

```

```{wpf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/Wpf/CartesianChart/FullyResponsive/FullyResponsiveExample.xaml.cs}

```

```{wf,!https://raw.githubusercontent.com/beto-rodriguez/Live-Charts/master/Examples/WinForms/Cartesian/FullyResponsive/FullyResponsive.cs}

```
