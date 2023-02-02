<!--

author:   Sebastian Zug, André Dietrich
email:    sebastian.zug@informatik.tu-freiberg.de & andre.dietrich@informatik.tu-freiberg.de
version:  0.0.1
language: en
narrator: Deutsch Female

import:   https://raw.githubusercontent.com/liaTemplates/AVR8js/main/README.md
          https://raw.githubusercontent.com/liascript-templates/plantUML/master/README.md
          https://github.com/LiaTemplates/PeriodicTable/blob/main/README.md
          https://github.com/LiaTemplates/Pyodide
          https://github.com/liascript/CodeRunner
          https://raw.githubusercontent.com/liaTemplates/vtk/master/README.md
-->

# Example Course

This course illustrates the export of LiaScript based learning content. The different formates are available in the `export` folder of the project.

Visit the youtube channel of LiaScript to get an overview about already implemented features.

!?[LiaScript](https://www.youtube.com/watch?v=vogB3gKlszM&t=70s)

## Interactive Tables

Click to `Bar chart` for visualizing diagram's content.

| Animal          | weight in kg | Lifespan years | Mitogen |
| --------------- | ------------:| --------------:| -------:|
| Mouse           |        0.028 |             02 |      95 |
| Flying squirrel |        0.085 |             15 |      50 |
| Brown bat       |        0.020 |             30 |      10 |
| Sheep           |           90 |             12 |      95 |
| Human           |           68 |             70 |      10 |

> More information about interactive tables are available [here](https://liascript.github.io/course/?https://raw.githubusercontent.com/liaScript/docs/master/README.md#122)

## Quizzes

What is the derivative function of $f(x) = x^6$?

[[ $f'(x) = 6$ | ( $f'(x) = 6x^5$ ) | $f'(x) = 5x^6$ ]]

What is $37 + 15$?

[[52]]
[[?]] the solution is larger than 50
[[?]] it is less than 55
[[?]] it should be an even number
***********************************************************************

52 is the correct solution, you get this by adding:

``` ascii
                        .------.
                        |      |
                        |      v
                        |
                        |     (1)
  37           3(7)     |     (3)x          37
+ 15         + 1(5)     |   + (1)x        + 15
---- -->     ------ --> |   ------ -->    ----
  ??           (12)     |     (5)2          52
                |       |                 ====
                '-------'
                  carry                                                        
```

***********************************************************************

> More information about quizzes are available [here](https://liascript.github.io/course/?https://raw.githubusercontent.com/liaScript/docs/master/README.md#60)

## Executable and editable Codes

js based interpreters
=========================

```python   PlotSin.py
import numpy as np
import matplotlib.pyplot as plt

t = np.arange(0.0, 2.0, 0.01)
s = np.sin(2 * np.pi * t)

fig, ax = plt.subplots()
ax.plot(t, s)

ax.grid(True, linestyle='-.')
ax.tick_params(labelcolor='r', labelsize='medium', width=3)

plt.show()

plot(fig) # <- this is required to plot the fig also on the LiaScript canvas
```
@Pyodide.eval

> More information about the Pyodide plugin are available [here](https://liascript.github.io/course/?https://github.com/LiaTemplates/pyodide)

Server based compiling and execution
=========================

```csharp Program.cs
using System;
using System.Collections.Generic;
using System.Collections;
using System.Linq;
using System.Text;

int n;
Console.Write("Number of primes: ");
n = int.Parse(Console.ReadLine());

ArrayList primes = new ArrayList();
primes.Add(2);

for(int i = 3; primes.Count < n; i++) {
	bool isPrime = true;
	foreach(int num in primes) isPrime &= i % num != 0;
	if(isPrime) primes.Add(i);
}

Console.Write("Primes: ");
foreach(int prime in primes) Console.Write($" {prime}");
```
```xml  project.csproj
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net6.0</TargetFramework>
  </PropertyGroup>
</Project>
```
@LIA.eval(`["Program.cs", "project.csproj"]`, `dotnet build -nologo`, `dotnet run -nologo`)

> More information about the Coderunner plugin are available [here](https://github.com/liascript/CodeRunner)

## Diagrams and Schemas

Software development
=========================

```text PlantUML.txt
@startuml

abstract class AbstractList
abstract AbstractCollection
interface List
interface Collection

List <|-- AbstractList
Collection <|-- AbstractCollection

Collection <|- List
AbstractCollection <|- AbstractList
AbstractList <|-- ArrayList

class ArrayList {
  Object[] elementData
  size()
}

enum TimeUnit {
  DAYS
  HOURS
  MINUTES
}

annotation SuppressWarnings

@enduml
```
@plantUML.eval(png)

> More information about this plugin are available [here](https://liascript.github.io/course/?https://raw.githubusercontent.com/liascript-templates/plantUML/master/README.md#1)

Chemistry
=========================

@PeriodicTable

## Simulations

Embedded Systems
=========================

Run an Arduino example by clicking the button below the code. Adapt the content for changing the light pattern.

<div id="example1">
<wokwi-led color="red"   pin="13" label="13"></wokwi-led>
<wokwi-led color="green" pin="12" label="12"></wokwi-led>
<wokwi-led color="blue"  pin="11" label="11"></wokwi-led>
<wokwi-led color="blue"  pin="10" label="10"></wokwi-led>
<span id="simulation-time"></span>
</div>

```cpp    ExtendedHelloWorld.cpp
byte leds[] = {13, 12, 11, 10};
void setup() {
  Serial.begin(115200);
  for (byte i = 0; i < sizeof(leds); i++) {
    pinMode(leds[i], OUTPUT);
  }
}

int i = 0;
void loop() {
  Serial.print("LED: ");
  Serial.println(i);
  digitalWrite(leds[i], HIGH);
  delay(250);
  digitalWrite(leds[i], LOW);
  i = (i + 1) % sizeof(leds);
}
```
@AVR8js.sketch

> More information about the AVR8js plugin are available [here](https://liascript.github.io/course/?https://raw.githubusercontent.com/liaTemplates/AVR8js/main/README.md)

## Visualization

> __Note:__ This might take a while, to load and render the vti data set within the browser.

Examine the 3D object by mouse movements and clicks.

@VTK.load(https://data.kitware.com/api/v1/file/58e665158d777f16d095fc2e/download)

> More information about the VTK plugin are available [here](https://liascript.github.io/course/?https://raw.githubusercontent.com/liaTemplates/vtk/master/README.md#1)
