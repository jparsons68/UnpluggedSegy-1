# SEG-Y Reading Library in C# #

SEG-Y is a file format for seismic image data.  It is also known as SEGY or SGY.

Issues and sample data welcome. 

### Example

```C#
using System;
using Unplugged.Segy;
```

```C#
var reader = new SegyReader();
ISegyFile line = reader.Read(@"RMOTC Seismic data set\2D_Seismic\NormalizedMigrated_segy\lineA.sgy");
ITrace trace = line.Traces[0];
double mean = 0;
double max = double.MinValue;
double min = double.MaxValue;
foreach (var sampleValue in trace.Values)
{
    mean += sampleValue / trace.Values.Count;
    if (sampleValue < min) min = sampleValue;
    if (sampleValue > max) max = sampleValue;
}
Console.WriteLine(min);
Console.WriteLine(max);
Console.WriteLine(mean);
```

### Acknowledgements

Example data is courtesy of the [Rocky Mountian Oilfield Testing Center](http://www.rmotc.doe.gov/) and the U.S. Department of Energy

Resources on the SEG-Y format:

   - http://walter.kessinger.com/work/segy.html
   - http://en.wikipedia.org/wiki/SEG_Y
   - http://www.seg.org/documents/10161/77915/seg_y_rev1.pdf
