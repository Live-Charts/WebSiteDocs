# Install

UWP does not support all the features WPF does yet.{uwp,.doc-alert}

This article was built using visual studio2015, off-line installation help? 
[try this guide](http://stackoverflow.com/questions/8120289/is-there-a-way-to-download-packages-from-nuget-org-then-do-an-offline-installati).{.doc-alert}

Install using the [package manager console](https://docs.nuget.org/ndocs/tools/package-manager-console#installing-a-package):

PM> Install-Package LiveCharts.Wpf{wpf,.console}

PM> Install-Package LiveCharts.Uwp{uwp,.console}

PM> Install-Package LiveCharts.WinForms{wf,.console}

Or go to the Solution Explorer, right click on references, then Manage NuGet Packages...

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/managenuget.png)

Browse for **LiveCharts.Wpf{ wpf }** **LiveCharts.Uwp{ uwp }** **LiveCharts.WinForms{ wf }** 
select the package and click on install.

![](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/browseNuget.png)

Add namespace to your XAML{ wpf||uwp }

```{wpf}
xmlns:lvc="clr-namespace:LiveCharts.Wpf;assembly=LiveCharts.Wpf"
```

```{uwp}
xmlns:lvc="using:LiveCharts.Uwp"
```

Add namespaces to code behind

```{wpf}
using LiveCharts;
using LiveCharts.Wpf;
```

```{?uwp}
using LiveCharts;
using LiveCharts.Uwp;
```

Notice the WinForms version is based on WPF rendering engine, so you are running 
the WPF package with a wrapper for Windows Forms, therefore you need 3 namespaces{wf}

```{wf}
using LiveCharts; //Core of the library
using LiveCharts.Wpf; //The WPF controls
using LiveCharts.WinForms //the WinForm wrappers
```

Now you can add the charts to your toolbox as any WinForms control, After the package was installed correctly, go to *Build* menu, then *Rebuild Solution*, this will create the LiveCharts.WinForms.dll file in your project directory.{wf}

In the designer, open your toolbox, right click on it, then *Choose Items*{wf}

![{wf}](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/toolboxchooseitems.png)

At *.Net Framework Components* click on browse{wf}

![{wf}](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/browsecomponents.png)

​    

Browse for *LiveCharts.WinForms.dll* file, select it and then click *Open*, the file is normally located at *ProjectLocation/bin/Debug*{wf}

![{wf}](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/winformsdll.png)

In the *Choose Toolbox Items* dialog click OK to add the LiveCharts controls to your project.{wf}

That's all, now you should see at least 3 new controls in your toolbox, *CartesianChart*,
*PieChart* and *Gauge*, drag them to any form as any other control.{wf}

![{wf}](https://raw.githubusercontent.com/Live-Charts/WebSiteDocs/master/v1/Resources/toolboxinstalled.png)