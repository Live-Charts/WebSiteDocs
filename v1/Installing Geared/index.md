﻿<h3 class="important-tittle">Installing Geared Package</h3>

<p>
    Before installing the package, ensure it fills your needs, to test the package,
    <a href="/Content/ExampleApp.zip">download ExampleApp.zip</a>, unpack it and run
    ExampleApp.exe, the applications guides you on how to test it, you can find the source code
    of ExampleApp.exe <a href="https://github.com/Live-Charts/GearedExamples">here</a>, notice that
    by cloning the repository you cold start your trial period.
</p>

<p>
    Installing the Geared Values package is really simple, and you don't need to learn anything new to
    use it, you have a 10 day free trail, the trial requires an internet connection.
</p>

<p>
    From the Package Manager console:
</p>

<div class="row">
    <div class="col-md-offset-2 col-md-8">
        <div class="spaced panel console card-shadow">
            <div class="panel-body">
                <h3 class="spaced text-center">PM> Install-Package LiveCharts.Geared</h3>
            </div>
        </div>
    </div>
</div>

<p>
    And that's all, now you applications contains two new features:
</p>

<h4>1. An extra set of series</h4>

<p>
    A set of 12 light and fast series to use them with the CartesianChart class, it includes
    a geared version of all the series supported by the library, but HeatSeries (in version 1.2, version 1.3
    will include the heat series), how much is faster? please play with
    ExampleApp as explained at the top of this page, in the better case it can render 10 million points in
    less than a second, here is a small snipped comparing a Geared and non Geared code
</p>

<pre class="prettyprint">using LiveCharts;
using LiveCharts.Geared;

MyChart.Series = new SeriesCollection
{
    new GLineSeries
    {
        Values = new GearedValues&lt;double> {7,4,9, ... }
    }
};
</pre>

<h4>2. A smarter values instance</h4>

<p>
    Instead of using the classic <i class="text-muted">ChartValues</i>, you can use the <i class="text-muted">GearedValues</i> class, it is smart
    enough to optimize your data according to many variables, such as the chart size, the series type
    and finally the quality you set, this class allows you to reduce the accuracy of your plot to gain
    performance, for example in the next case imagine you are using
    a line series, and you only care about the trend of your line, then you can use the <b>low</b> quality to
    render it faster, the error of the lower quality is 10px, but in an opposite case, you care about accuracy,
    then you must use the <b>highest</b> quality, the rendering time will be slower, but you won't have any visual error,
    there are also 2 more available qualities, <b>medium</b> quality, with a max error of 5px, and <b>high</b>
    which is the default quality, it has a practically invisible max error of 2px.
</p>

<p>
    Using LiveCharts.Geares is easy, you need to use the geared version of the series you need, and use <i class="text-muted">GearedValues</i>
    instead of <i class="text-muted">ChartValues</i>, so any example in this web site applies to the geared package, following this simple rule,
    the next code compares a chart without and with the geared values package.
</p>

<p><b>Code Behind</b></p>

<div class="row">
    <div class="col-md-6">
        <h4 class="text-center">Without Geared Package</h4>
        <pre class="prettyprint">using LiveCharts;


namespace samples
{
  public partial class Window 
  {
    public Window()
    {
      InitializeComponents();
      

      Values = new ChartValue&lt;double>{1,2,3, ..., 100000};


      DataContext = this;
    }

    public ChartValues&lt;double> Values { get; set; }
  }
}</pre>
    </div>
    <div class="col-md-6">
        <h4 class="text-center">With Geared Package</h4>
        <pre class="prettyprint">using LiveCharts;
using Livecharts.Geared; //added name space

namespace samples
{
  public partial class Window 
  {
    public Window()
    {
      InitializeComponents();
      
      //using geared values instead
      Values = new GearedValues&lt;double>{1,2,3, ..., 100000};
      //set the quality according to your needs
      Values.WithQuality(Quality.Highest);
      DataContext = this;
    }
    //Replaced ChartValues with GearedValues
    public GearedValues&lt;double> Values { get; set; }
  }
}</pre>
    </div>
</div>

<p><b>XAML</b></p>

<div class="row">
    <div class="col-md-6">
        <h4 class="text-center">Without Geared Package</h4>
        <pre class="prettyprint">&lt;Window x:Class="Wpf.Window"
        xmlns="..."
        xmlns:lvc="clr-namespace:LiveCharts.Wpf;assembly=LiveCharts.Wpf">

    &lt;Grid>
        &lt;lvc:CartesianChart>
            &lt;lvc:CartesianChart.Series>

                &lt;lvc:LineSeries Values="{Binding Values}" />
            &lt;/lvc:CartesianChart.Series>
        &lt;/lvc:CartesianChart>
    &lt;/Grid>
&lt;/Window></pre>
    </div>
    <div class="col-md-6">
        <h4 class="text-center">With Geared Package</h4>
        <pre class="prettyprint">&lt;Window x:Class="Wpf.Window"
        xmlns="..."
        xmlns:lvc="clr-namespace:LiveCharts.Wpf;assembly=LiveCharts.Wpf"
        xmlns:geared="clr-namespace:LiveCharts.Geared;assembly=LiveCharts.Geared">
    &lt;Grid>
        &lt;lvc:CartesianChart>
            &lt;lvc:CartesianChart.Series>
                &lt;!--Notice we are using GLineSeries, instead of LineSeries-->
                &lt;geared:GLineSeries Values="{Binding Values}" />
            &lt;/lvc:CartesianChart.Series>
        &lt;/lvc:CartesianChart>
    &lt;/Grid>
&lt;/Window></pre>
    </div>
</div>

<p>
    And that's it, you are running Livecharts.Geared
</p>
