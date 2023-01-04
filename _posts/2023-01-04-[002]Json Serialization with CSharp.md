# How to Json Serialization with CSharp


<a href=https://jupyter-notebook.readthedocs.io/en/stable/>"ReadTheDocs"</a><br/>
<a href=https://www.math.ubc.ca/~pwalls/math-python/jupyter/latex/>"Math Latex"</a><br/>

<a href="#Nuget-Package-Installation">Nuget Package Installation</a><br/>
<a href="#Reference-to-Newtonsoft.Json">Reference to Newtonsoft.Json</a><br/>
<a href="#Define-C#-Object">Define C# Object</a><br/>
<a href="#Serialize-Simple-Object-Demo">Serialize Simple Object Demo</a><br/>
<a href="#Serialize-Full-Object-Demo">Serialize Full Object Demo</a><br/><br/>




<hr style="border:10px solid #ffbbaa"/>

# Nuget Package Installation

<details>
<summary><font color=red>Detail View</font></summary>
    
In order to **Serialize** C# Object to Json string or **Deserialize** Json string to C# Object, <br/>
firstly install NewtonSoft.Json Nuget Package.

### Nuget Package Installation for "Newtonsoft.Json"
```CSharp
#r "Newtonsoft.Json"
```
<br/>
</details>

<hr style="border:1px solid blue">
<div style="text-align:right">[<a href="#How-to-Json-Serialization-with-CSharp">Back to Top</a>]</div><br/>




<hr style="border:10px solid #ffbbaa"/>

# Reference to Newtonsoft.Json

<details>
<summary><font color=red>Detail View</font></summary>
    
In order to use *Newtonsoft.Json* Package<br/>
**using** statement must be described.

```CSharp
using Newtonsoft.Json;
```

<br/>
</details>
<hr style="border:1px solid blue">
<div style="text-align:right">[<a href="#How-to-Json-Serialization-with-CSharp">Back to Top</a>]</div><br/>



```C#
#r "Newtonsoft.Json"

using Newtonsoft.Json;
using System.Collections;
```



<hr style="border:10px solid #ffbbaa"/>

# Define C# Object

<details>
    <summary><font color=red>Detail View</font></summary>

Define Simple class which has just 4 simple string properties<br/>
This simple class will have just **Column name** information not the **Data**

```CSharp
public class MGPS
{
    public List<string> Anode {get; set;}        // "[CU1, AL1, CU2, AL2, ...]" 
    public List<string> SeaChest {get; set;}     // "[SCU, SCUHigh, SCULow, ...]"
}
```
<br/>

</details>

<hr style="border:1px solid blue">
<div style="text-align:right">[<a href="#How-to-Json-Serialization-with-CSharp">Back to Top</a>]</div><br/>



```C#
// class Definition for C# Object
public class MGPS
{
    public List<string> Anode {get; set;}        // "[CU1, AL1, CU2, AL2, ...]" 
    public List<string> SeaChest {get; set;}     // "[SCU, SCUHigh, SCULow, ...]"
}

public class HosunLog
{
    public List<string> CN_Basic {get; set;}
    public List<string> CN_Maintenance {get; set;}
    public List<string> CN_Capacity {get; set;}
    public List<string> CN_Default {get; set;}
    public List<List<string>> CN_ICCP {get; set;}
    public MGPS CN_MGPS {get; set;}
    public List<string> CN_Shaft {get; set;}
}
```



<hr style="border:10px solid #ffbbaa"/>

# Serialize Simple Object Demo

<details>
    <summary><font color=red>Detail View</font></summary>
Initialize MGPS Type mgps instance like below:

```CSharp
MGPS mgps = new MGPSMGPS()
{
    Anode = new List<string> {
        "CU1", "AL1", "CU2", "AL2"
    },
    SeaChest = new List<string> {
        "SeaChest"
    }
};
```
<br/>

Inorder to indedted format of Json string for  legibility,<br/>
use <font color=green>*Formatting.Indented*</font> option in the 
<font color=red>**JsonConvert.SerializeObject(**</font><font color=green> _instance_</font>, <font color=green>_option_</font><font color=red> **)**</font> method

</details>


<hr style="border:1px solid blue"/>
<div style="text-align:right">[<a href="#How-to-Json-Serialization-with-CSharp">Back to Top</a>]</div>


```C#
// Define C# Object(Instance)
MGPS mgps = new MGPS()
{
    Anode = new List<string> {
        "CU1", "AL1", "CU2", "AL2"
    },
    SeaChest = new List<string> {
        "SeaChest"
    }
};

// Serialize C# Object to Json string
string jsonMGPSString = JsonConvert.SerializeObject(mgps, Formatting.Indented);
```


```C#
jsonMGPSString
```




    {
      "Anode": [
        "CU1",
        "AL1",
        "CU2",
        "AL2"
      ],
      "SeaChest": [
        "SeaChest"
      ]
    }





<hr style="border:10px solid #ffbbaa"/>

# Serialize Full Object Demo

<details>
    <summary><font color=red>Detail View</font></summary>

Initialize HosunLog Type Log instance like below:
```CSharp
HosunLog Log = new HosunLog()
{
    CN_Basic = new List<string> { 
        "VesselName", "ProjectNumber", "Owner", null 
    },
    CN_Maintenance = new List<string> {
        "LastDrydock", "NextDrydock", "LastBrush", "AnodePeriod" 
    },
    CN_Capacity = new List<string> {
        "AFTAmpDesign", "AFTVoltDesign", "FWDAmpDesign", "FWDVoltDesign" 
    },
    CN_Default = new List<string> {
        "Date", "Location", "Draft", "SeaTemp"
    },
    CN_ICCP = new List<List<string>> {
        new List<string> { "AFTAmp", "AFTVolt", "AFTCell1", "AFTCell2"}, 
        new List<string> { "FWDAmp", "FWDVolt", "FWDCell1", "FWDCell2"}
    },
    CN_MGPS = new MGPS() {
        Anode = new List<string> {"CU1", "AL1", "CU2", "AL2"},
        SeaChest = new List<string> {"SeaChest"}
    },
    CN_Shaft = new List<string> {
        "Shaft" 
    }
};
```
<br/>

</details>

<hr style="border:1px solid blue"/>
<div style="text-align:right">[<a href="#How-to-Json-Serialization-with-CSharp">Back to Top</a>]</div>


```C#
// Define C# Object(Instance)
HosunLog Log = new HosunLog()
{
    CN_Basic = new List<string> {
        "VesselName", "ProjectNumber", "Owner", null 
    },
    CN_Maintenance = new List<string> {
        "LastDrydock", "NextDrydock", "LastBrush", "AnodePeriod" 
    },
    CN_Capacity = new List<string> {
        "AFTAmpDesign", "AFTVoltDesign", "FWDAmpDesign", "FWDVoltDesign" 
    },
    CN_Default = new List<string> {
        "Date", "Location", "Draft", "SeaTemp"
    },
    CN_ICCP = new List<List<string>> {
        new List<string> { "AFTAmp", "AFTVolt", "AFTCell1", "AFTCell2"}, 
        new List<string> { "FWDAmp", "FWDVolt", "FWDCell1", "FWDCell2"}
    },
    CN_MGPS = new MGPS() {
        Anode = new List<string> {"CU1", "AL1", "CU2", "AL2"},
        SeaChest = new List<string> {"SeaChest"}
    },
    CN_Shaft = new List<string> {
        "Shaft" 
    }
};

// Serialize C# Object to Json string.
string jsonString = JsonConvert.SerializeObject(Log, Formatting.Indented);
```


```C#
jsonString
```




    {
      "CN_Basic": [
        "VesselName",
        "ProjectNumber",
        "Owner",
        null
      ],
      "CN_Maintenance": [
        "LastDrydock",
        "NextDrydock",
        "LastBrush",
        "AnodePeriod"
      ],
      "CN_Capacity": [
        "AFTAmpDesign",
        "AFTVoltDesign",
        "FWDAmpDesign",
        "FWDVoltDesign"
      ],
      "CN_Default": [
        "Date",
        "Location",
        "Draft",
        "SeaTemp"
      ],
      "CN_ICCP": [
        [
          "AFTAmp",
          "AFTVolt",
          "AFTCell1",
          "AFTCell2"
        ],
        [
          "FWDAmp",
          "FWDVolt",
          "FWDCell1",
          "FWDCell2"
        ]
      ],
      "CN_MGPS": {
        "Anode": [
          "CU1",
          "AL1",
          "CU2",
          "AL2"
        ],
        "SeaChest": [
          "SeaChest"
        ]
      },
      "CN_Shaft": [
        "Shaft"
      ]
    }




```C#

```
