```C#
#r "Newtonsoft.Json"
using Newtonsoft.Json;
using System.Collections;
```


```C#
public class MGPS
{
    public List<string> Anode {get; set;}        // "[CU1, AL1, CU2, AL2, ...]" 
    public List<string> SeaChest {get; set;}     // "[SCU, SCUHigh, SCULow, ...]"
}
public class Capacity
{
    public List<string> Single {get; set;}
    public List<string> AFT {get; set;}
    public List<string> FWD {get; set;}
}
public class ICCP
{
    public List<string> Single {get; set;}
    public List<string> AFT {get; set;}
    public List<string> FWD {get; set;}
}
public class HosunLog
{
    public List<string> CN_Basic {get; set;}
    public List<string> CN_Maintenance {get; set;}
    public Capacity CN_Capacity {get; set;}
    public List<string> CN_Default {get; set;}
    public ICCP CN_ICCP {get; set;}
    public MGPS CN_MGPS {get; set;}
    public List<string> CN_Shaft {get; set;}
}
```


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




```C#
string jsonRead = @"{
  'Anode': [
    'CU1',
    'AL1',
    'CU2',
    'AL2'
  ],
  'SeaChest': [
    'SeaChest'
  ]
}";
```


```C#
MGPS mgps2 = JsonConvert.DeserializeObject<MGPS>(jsonRead);
```


```C#
foreach(var item in mgps2.Anode)
{
    Console.WriteLine(item);
}

foreach(var item in mgps2.SeaChest)
{
    Console.WriteLine(item);
}
```

    CU1
    AL1
    CU2
    AL2
    SeaChest
    


```C#

```


```C#

```


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
    CN_Capacity = new Capacity() {
        Single = null,
        AFT = new List<string> { "AmpDesign", "VoltDesign"},
        FWD = new List<string> { "AmpDesign", "VoltDesign"} 
    },
    CN_Default = new List<string> {
        "Date", "Location", "Draft", "SeaTemp"
    },
    CN_ICCP = new ICCP() {
        Single = null, 
        AFT = new List<string> { "Amp", "Volt", "Cell1", "Cell2" },
        FWD = new List<string> { "Amp", "Volt", "Cell1", "Cell2" }
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
// print out Serialized Json string
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
      "CN_Capacity": {
        "Single": null,
        "AFT": [
          "AmpDesign",
          "VoltDesign"
        ],
        "FWD": [
          "AmpDesign",
          "VoltDesign"
        ]
      },
      "CN_Default": [
        "Date",
        "Location",
        "Draft",
        "SeaTemp"
      ],
      "CN_ICCP": {
        "Single": null,
        "AFT": [
          "Amp",
          "Volt",
          "Cell1",
          "Cell2"
        ],
        "FWD": [
          "Amp",
          "Volt",
          "Cell1",
          "Cell2"
        ]
      },
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
// Hard code input string for Deserialization.
string jsonHosunRead = @"
{
  'CN_Basic': [
    'VesselName',
    'ProjectNumber',
    'Owner',
    null
  ],
  'CN_Maintenance': [
    'LastDrydock',
    'NextDrydock',
    'LastBrush',
    'AnodePeriod'
  ],
  'CN_Capacity': {
    'Single':null,
    'AFT': [
      'AmpDesign',
      'VoltDesign'
    ],
    'FWD': [
      'AmpDesign',
      'VoltDesign'
    ]
  },
  'CN_Default': [
    'Date',
    'Location',
    'Draft',
    'SeaTemp'
  ],
  'CN_ICCP': {
    'Single': null,
    'AFT': [
      'Amp',
      'Volt',
      'Cell1',
      'Cell2'
    ],
    'FWD': [
      'Amp',
      'Volt',
      'Cell1',
      'Cell2'
    ]
  },
  'CN_MGPS': {
    'Anode': [
      'CU1',
      'AL1',
      'CU2',
      'AL2'
    ],
    'SeaChest': [
      'SeaChest'
    ]
  },
  'CN_Shaft': [
    'Shaft'
  ]
}
";
```


```C#
// Deserialization to HosunLog type instance hosun.
HosunLog hosun = JsonConvert.DeserializeObject<HosunLog>(jsonHosunRead);
```


```C#
// print out hosun (check out hosun's structure)
hosun
```




<table><thead><tr><th>CN_Basic</th><th>CN_Maintenance</th><th>CN_Capacity</th><th>CN_Default</th><th>CN_ICCP</th><th>CN_MGPS</th><th>CN_Shaft</th></tr></thead><tbody><tr><td><div class="dni-plaintext">[ VesselName, ProjectNumber, Owner, &lt;null&gt; ]</div></td><td><div class="dni-plaintext">[ LastDrydock, NextDrydock, LastBrush, AnodePeriod ]</div></td><td><div class="dni-plaintext">{ Submission#55+Capacity: Single: &lt;null&gt;, AFT: [ AmpDesign, VoltDesign ], FWD: [ AmpDesign, VoltDesign ] }</div></td><td><div class="dni-plaintext">[ Date, Location, Draft, SeaTemp ]</div></td><td><div class="dni-plaintext">{ Submission#55+ICCP: Single: &lt;null&gt;, AFT: [ Amp, Volt, Cell1, Cell2 ], FWD: [ Amp, Volt, Cell1, Cell2 ] }</div></td><td><div class="dni-plaintext">{ Submission#55+MGPS: Anode: [ CU1, AL1, CU2, AL2 ], SeaChest: [ SeaChest ] }</div></td><td><div class="dni-plaintext">[ Shaft ]</div></td></tr></tbody></table>




```C#
hosun.CN_Basic
```




<table><thead><tr><th><i>index</i></th><th>value</th></tr></thead><tbody><tr><td>0</td><td>VesselName</td></tr><tr><td>1</td><td>ProjectNumber</td></tr><tr><td>2</td><td>Owner</td></tr><tr><td>3</td><td><div class="dni-plaintext">&lt;null&gt;</div></td></tr></tbody></table>




```C#
hosun.CN_Maintenance
```




<table><thead><tr><th><i>index</i></th><th>value</th></tr></thead><tbody><tr><td>0</td><td>LastDrydock</td></tr><tr><td>1</td><td>NextDrydock</td></tr><tr><td>2</td><td>LastBrush</td></tr><tr><td>3</td><td>AnodePeriod</td></tr></tbody></table>




```C#
hosun.CN_Capacity
```




<table><thead><tr><th>Single</th><th>AFT</th><th>FWD</th></tr></thead><tbody><tr><td><div class="dni-plaintext">&lt;null&gt;</div></td><td><div class="dni-plaintext">[ AmpDesign, VoltDesign ]</div></td><td><div class="dni-plaintext">[ AmpDesign, VoltDesign ]</div></td></tr></tbody></table>




```C#
hosun.CN_Default
```




<table><thead><tr><th><i>index</i></th><th>value</th></tr></thead><tbody><tr><td>0</td><td>Date</td></tr><tr><td>1</td><td>Location</td></tr><tr><td>2</td><td>Draft</td></tr><tr><td>3</td><td>SeaTemp</td></tr></tbody></table>




```C#
hosun.CN_ICCP
```




<table><thead><tr><th>Single</th><th>AFT</th><th>FWD</th></tr></thead><tbody><tr><td><div class="dni-plaintext">&lt;null&gt;</div></td><td><div class="dni-plaintext">[ Amp, Volt, Cell1, Cell2 ]</div></td><td><div class="dni-plaintext">[ Amp, Volt, Cell1, Cell2 ]</div></td></tr></tbody></table>




```C#
hosun.CN_MGPS
```




<table><thead><tr><th>Anode</th><th>SeaChest</th></tr></thead><tbody><tr><td><div class="dni-plaintext">[ CU1, AL1, CU2, AL2 ]</div></td><td><div class="dni-plaintext">[ SeaChest ]</div></td></tr></tbody></table>




```C#
hosun.CN_Shaft
```




<table><thead><tr><th><i>index</i></th><th>value</th></tr></thead><tbody><tr><td>0</td><td>Shaft</td></tr></tbody></table>




```C#

```
