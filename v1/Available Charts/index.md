# Available Charts

### Cartesian Chart

 The *Cartesian Chart* class allows you to plot any series that uses a *cartesian coordinate system*, every point is a pair of values (*X*, *Y*), it supports many series, you can combine any of these seriesin the same plot:

<div class="row spaced">

<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 text-center">
<div>Line Series</div>
![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/lineSeries.jpg)
</div>

<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 text-center">
<div>Vertical Line Series</div>
![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/verticallineseries.jpg)
</div>

<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 text-center">
<div>Column Series</div>
![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/columnseries.jpg)
</div>

<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 text-center">
<div>Row Series</div>
![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/rowseries.jpg)
</div>

<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 text-center">
<div>Stacked Area Series</div>
![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/stackedareaseries.jpg)
</div>

<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 text-center">
<div>Vertical Stacked Area Series</div>
![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/verticalstackedareaseries.jpg)
</div>

<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 text-center">
<div>Stacked Column Series</div>
![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/stackedcolumnseries.jpg)
</div>

<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 text-center">
<div>Stacked Row Series</div>
![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/stackedrowsseries.jpg)
</div>

<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 text-center">
<div>Heat Series</div>
![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/Heat%20Series.jpg)
</div>

<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 text-center">
<div>OHCLand Candle Series</div>
![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/ohclseries.jpg)
</div>

<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 text-center">
<div>Bubbles Series</div>
![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/buubleseries.jpg)
</div>

<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 text-center">
<div>StepLine Series</div>
![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/stepline.png)
</div>
</div>

Here is an example, notice some series use a specialized point, LiveCharts already knows how to plot many types, if you need to define your own, please take a read at  <a href="/App/Examples/v1/{{sms.platform}}/Types and Mappers">Types and Mappers</a> article.

```
using LiveCharts;
using LiveCharts.Defaults; //Contains the already defined types

LiveCharts.SeriesCollection series = new LiveCharts.SeriesCollecion 
{
  new LineSeries
  {
    //The ObservableValue class notifies the chart to update when value changes

    Values = new ChartValues&lt;LiveCharts.Defaults.ObservableValue&gt;
    {
        new LiveCharts.Defaults.ObservableValue(4),
        new LiveCharts.Defaults.ObservableValue(4),
        // ...
    }
  },
  new ColumnSeries
  {
    Values = new ChartValues&lt;ObservableValue&gt;
    {
      new ObservableValue(4),
      new ObservableValue(2),
      // ...
    }
  },
  new OhlcSeries
  {
    Values = new ChartValues&lt;OhlcPoint&gt;
    {
      new OhlcPoint(32, 35, 30, 32),
      new OhlcPoint(33, 38, 31, 37),
      // ..
    }
  }
}
```
### Pie Chart

Use it to plot pies and doughnuts

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/doughnut.jpg)

### Gauge

It has 2 modes, 180 and 360 degrees, useful to display progress or completion.

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/gauges.png)

### Angular Gauge

Use it to display the current value in a range.

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/angulargauge.jpg)

### Maps

LiveCharts also support geo heat maps, they compare the values according to geographic zone.

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/geomap.png)