# Install

UWP does not support all the features WPF does yet.{ ?uwp, .doc-alert }

This article was built using visual studio2015, off-line installation help? 
[try this guide](http://stackoverflow.com/questions/8120289/is-there-a-way-to-download-packages-from-nuget-org-then-do-an-offline-installati).{.doc-alert}

Install using the <a href="https://docs.nuget.org/ndocs/tools/package-manager-console#installing-a-package">package manager console</a>:{}

### PM> Install-Package LiveCharts.Wpf{ ?wpf }
### PM> Install-Package LiveCharts.Uwp{ ?uwp }
### PM> Install-Package LiveCharts.WinForms{ ?wf }

Or go to the Solution Explorer, right click on references, then Manage NuGet Packages...

![](/v1/Install/managenuget.png)

Browse for **LiveCharts.Wpf{ ?wpf }** **LiveCharts.Uwp{ ?uwp }** **LiveCharts.WinForms{ ?wf }** 
select the package and click on install.

![]()

![]({{source}}/v1/Install/browseNuget.png)

Add namespace to your XAML{ ?wpf||uwp }

```{?wpf}
xmlns:lvc="clr-namespace:LiveCharts.Wpf;assembly=LiveCharts.Wpf"
```

```{?uwp}
xmlns:lvc="using:LiveCharts.Uwp"
```

Add namespaces to code behind

```{?wpf}
using LiveCharts;
using LiveCharts.Wpf;
```

```{?uwp}
using LiveCharts;
using LiveCharts.Uwp;
```

Notice the WinForms version is based on WPF rendering engine, so you are running 
the WPF package with a wrapper for Windows Forms, therefore you need 3 namespaces

```{?wf}
using LiveCharts; //Core of the library
using LiveCharts.Wpf; //The WPF controls
using LiveCharts.WinForms //the WinForm wrappers
```

<div ng-if="wf">
    <p>
        Now you can add the charts to your toolbox as any WinForms control, After the package was installed correctly,
        go to <i>Build</i> menu, then <i>Rebuild Solution</i>, this will create the LiveCharts.WinForms.dll file in
        your project directory.
    </p>
    <p>
        In the designer, open your toolbox, right click on it, then <i>Choose Items</i>
    </p>
    <div class="text-center">
        <img src="{{source}}/v1/Install/toolboxchooseitems.png"/>
    </div>
    <p>
        At <i>.Net Framework Components</i> click on browse
    </p>
    <div class="text-center">
        <img src="{{source}}/v1/Install/browsecomponents.png"/>
    </div>
    <p>
        Browse for <i>LiveCharts.WinForms.dll</i> file, select it and then click <i>Open</i>,
        the file is normally located at <i>ProjectLocation/bin/Debug</i>
    </p>
    <div class="text-center">
        <img src="{{source}}/v1/Install/winformsdll.png"/>
    </div>
    <p>
        In the <i>Choose Toolbox Items</i> dialog click OK to add the LiveCharts controls to your project.
    </p>
    <p>
        That's all, now you should see at least 3 new controls in your toolbox, <i>CartesianChart</i>,
        <i>PieChart</i> and <i>Gauge</i>, drag them to any form as any other control.
    </p>
    <div class="text-center">
        <img src="{{source}}/v1/Install/toolboxinstalled.png" />
    </div>
</div>


