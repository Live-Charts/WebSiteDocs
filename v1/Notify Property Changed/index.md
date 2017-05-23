# INotifyPropertyChanged

When you require a point to update automatically when a property changes, you must implement *INotifyPropertyChanged*, this interface is provided by the .Net framework, in this article we are building *ObservableValue* class from scratch, notice this class is already defined in the library, *INotifyPropertyChanged* is a common component of .Net framework, if you want to learn more about it, the web is full of articles, basically it is useful to rise an event every time a property changes.

Create a new class named *ObservableValue*, and add a property named *Value*

```
public class ObservableValue
{
    private double _value;

    public double Value
    {
        get { return _value; }
        set
        {
            _value = value;
        }
    }
}
```

Then implement *INotifyPropertyChanged*.

```
public class ObservableValue : INotifyPropertyChanged //added INotifyPropertyChanged
{
    private double _value;

    public double Value
    {
        get { return _value; }
        set
        {
            _value = value;
            OnPropertyChanged("Value");
        }
    }
    
    #region INotifyPropertyChangedImplementation
    
    public event PropertyChangedEventHandler PropertyChanged;
    
    protected virtual void OnPropertyChanged(string propertyName = null)
    {
        if (PropertyChanged != null) 
            PropertyChanged.Invoke(this, new PropertyChangedEventArgs(propertyName));
    }
    
    #endregion
}
```

Since this type is already defined in the library,  it has a mapper saved globally already, this mapper teach LiveCharts how it should pull out the *X* and *Y* coordinates, the already defined mapper goes as follows:

```
var mapper = Mappers.Xy&lt;ObservableValue>()
    .X((instance, index) => index)  // pull the index as our X coordinate
    .Y((instance, index) => instance.Value); // use the Value property as Y

// Finally we save the mapper globally
LiveCharts.Charting.For&lt;ObservableValue>(mapper);
```

And that's it, now the library knows how to plot the *ObservableValue* object, and this object also notifies the chart to update every time the *Value* property changes.