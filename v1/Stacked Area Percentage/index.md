  
<h4 class="important-tittle">Stacked Area</h4>

<p>
    Use the stacked area series to compare trends and the proportion of every series in the total,
    in this example we are stacking percentage instead of values, using the <i>StackMode</i> property
    notice in this example we are using the already defined DateTimePoint, LiveCharts already knows how to
    plot this type, but you could always
    <a href="/App/examples/v1/wpf/Types%20and%20Configuration">use your own type</a>.
</p>

<div class="text-center">
    <img src="/App/Examples/v1/Stacked Area Percentage/Images/stacked-percentage.jpg" />
</div>

<pre class="prettyprint">using System;
using System.Linq;
using System.Windows;
using System.Windows.Controls;
using LiveCharts;
using LiveCharts.Defaults;
using LiveCharts.Wpf;

namespace Wpf.CartesianChart.StackedArea
{
    public partial class StackedAreaExample : UserControl
    {
        public StackedAreaExample()
        {
            InitializeComponent();

            SeriesCollection = new SeriesCollection
            {
                new StackedAreaSeries
                {
                    Title = "Africa",
                    Values = new ChartValues&lt;DateTimePoint>
                    {
                        new DateTimePoint(new DateTime(1950, 1, 1), .228),
                        new DateTimePoint(new DateTime(1960, 1, 1), .285),
                        new DateTimePoint(new DateTime(1970, 1, 1), .366),
                        new DateTimePoint(new DateTime(1980, 1, 1), .478),
                        new DateTimePoint(new DateTime(1990, 1, 1), .629),
                        new DateTimePoint(new DateTime(2000, 1, 1), .808),
                        new DateTimePoint(new DateTime(2010, 1, 1), 1.031),
                        new DateTimePoint(new DateTime(2013, 1, 1), 1.110)
                    },
                    LineSmoothness = 0,
                    StackMode = StackMode.Percentage
                },
                new StackedAreaSeries
                {
                    Title = "N & S America",
                    Values = new ChartValues&lt;DateTimePoint>
                    {
                        new DateTimePoint(new DateTime(1950, 1, 1), .339),
                        new DateTimePoint(new DateTime(1960, 1, 1), .424),
                        new DateTimePoint(new DateTime(1970, 1, 1), .519),
                        new DateTimePoint(new DateTime(1980, 1, 1), .618),
                        new DateTimePoint(new DateTime(1990, 1, 1), .727),
                        new DateTimePoint(new DateTime(2000, 1, 1), .841),
                        new DateTimePoint(new DateTime(2010, 1, 1), .942),
                        new DateTimePoint(new DateTime(2013, 1, 1), .972)
                    },
                    LineSmoothness = 0,
                    StackMode = StackMode.Percentage
                },
                new StackedAreaSeries
                {
                    Title = "Asia",
                    Values = new ChartValues&lt;DateTimePoint>
                    {
                        new DateTimePoint(new DateTime(1950, 1, 1), 1.395),
                        new DateTimePoint(new DateTime(1960, 1, 1), 1.694),
                        new DateTimePoint(new DateTime(1970, 1, 1), 2.128),
                        new DateTimePoint(new DateTime(1980, 1, 1), 2.634),
                        new DateTimePoint(new DateTime(1990, 1, 1), 3.213),
                        new DateTimePoint(new DateTime(2000, 1, 1), 3.717),
                        new DateTimePoint(new DateTime(2010, 1, 1), 4.165),
                        new DateTimePoint(new DateTime(2013, 1, 1), 4.298)
                    },
                    LineSmoothness = 0,
                    StackMode = StackMode.Percentage
                },
                new StackedAreaSeries
                {
                    Title = "Europe",
                    Values = new ChartValues&lt;DateTimePoint>
                    {
                        new DateTimePoint(new DateTime(1950, 1, 1), .549),
                        new DateTimePoint(new DateTime(1960, 1, 1), .605),
                        new DateTimePoint(new DateTime(1970, 1, 1), .657),
                        new DateTimePoint(new DateTime(1980, 1, 1), .694),
                        new DateTimePoint(new DateTime(1990, 1, 1), .723),
                        new DateTimePoint(new DateTime(2000, 1, 1), .729),
                        new DateTimePoint(new DateTime(2010, 1, 1), .740),
                        new DateTimePoint(new DateTime(2013, 1, 1), .742)
                    },
                    LineSmoothness = 0,
                    StackMode = StackMode.Percentage
                }
            };

            XFormatter = val => new DateTime((long) val).ToString("yyyy");
            YFormatter = val => val.ToString("N") + " M";

            DataContext = this;
        }

        public SeriesCollection SeriesCollection { get; set; }
        public Func&lt;double, string> XFormatter { get; set; }
        public Func&lt;double, string> YFormatter { get; set; }

    }
}
</pre>
