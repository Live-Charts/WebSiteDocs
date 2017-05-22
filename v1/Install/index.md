# Install

UWP does not support all the features WPF does yet.{ng-if=uwp}

<div class="doc-alert">
    This article was built using visual studio 2015, off-line installation help? 
    <a href="http://stackoverflow.com/questions/8120289/is-there-a-way-to-download-packages-from-nuget-org-then-do-an-offline-installati">here</a>
</div>

Install using the <a href="https://docs.nuget.org/ndocs/tools/package-manager-console#installing-a-package">package manager console</a>:{}

<div class="row">
    <div class="col-md-offset-2 col-md-8 col-xs-12">
        <div class="card-shadow console">
            <div class="panel-body spaced">
                <h3 ng-if="wpf" class="text-center spaced">PM> Install-Package LiveCharts.Wpf</h3>
                <h3 ng-if="wf" class="text-center spaced">PM> Install-Package LiveCharts.WinForms</h3>
                <h3 ng-if="uwp" class="text-center spaced">PM> Install-Package LiveCharts.Uwp</h3>
            </div>
        </div>
    </div>
</div>

Or go to the Solution Explorer, right click on references, then Manage NuGet Packages…

<div class="text-center">
    <img src="{{source}}/v1/Install/managenuget.png" />
</div>

<p>
    Browse for 
    <span ng-if="wpf">LiveCharts.Wpf</span>
    <span ng-if="wf">LiveCharts.Winforms</span>
    <span ng-if="uwp">LiveCharts.Uwp</span>, 
    select the package and click on install
</p>

<div class="text-center">
    <img src="{{source}}/v1/Install/browseNuget.png" />
</div>

<div ng-if="wpf">
    <p>Add namespace to your XAML</p>
    
    <pre class="prettyprint">xmlns:lvc="clr-namespace:LiveCharts.Wpf;assembly=LiveCharts.Wpf"</pre>
    
    <p>And to code behind if necessary</p>
    
    <pre class="prettyprint">using LiveCharts;
using LiveCharts.Wpf;</pre>
</div>

<div ng-if="uwp">
    <p>Add namespace to your XAML</p>

    <pre class="prettyprint">xmlns:lvc="using:LiveCharts.Uwp"</pre>

    <p>And to code behind if necessary</p>

    <pre class="prettyprint">using LiveCharts;
using LiveCharts.Uwp;</pre>
</div>

<div ng-if="wf">
    <p>
        Add name spaces to you code if necessary, notice the WinForms version uses WPF advanced rendering system,
        so you are actually running the WPF package with a wrapper to create a Windows Forms user control class,
        therefore you need 3 name spaces
    </p>

    <pre class="prettyprint">using LiveCharts; //Core of the library
using LiveCharts.Wpf; //The WPF controls
using LiveCharts.WinForms //the WinForm wrappers</pre>

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


