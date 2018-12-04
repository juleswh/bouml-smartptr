# bouml-smartptr
A BOUML plug-out for using c++11 smart-pointers in UML relations

## Usage

### Build the plug-out

Open ```plugout-smartptr.prj``` in [BOUML][1], you just have to generate for C++ (tools > Generate C++, or ctrl+G).
The code will be put under ```plugout-smartptr/cpp```.
Then you need to generate to ```.pro``` file. In the BOUML project, find the artifact named ```executable``` (use Ctrl+F to search). Right-click on it, then "Tool > Generate .pro". Change the paths to wherever you want to (the default /tmp/ not a good idea). Click OK, and in a terminal go where the files where generated. Just run ```qmake && make```. If all the dependencies are ok, you now have the plugout executable.

### Import the profile

Now open your own project, and import the ```smartptr-profile.prj``` project, which will give you access to the new stereotypes for UML Relations: right-click on your top-level project > Import Project.
You also need to set the path to the plugout. In Tools > Tools Settings > Class, add a tool with the path to your freshly built plugout, and name it "C++ smart_ptr" (I don't if the name's actually important).

### Set-up generation options

Last thing to do is to tell the generator which includes are needed for your stereotypes.
In your top-level package Generation Settings > Stereotypes > attribute and relations stereotypes correspondance, add the following lines:

| Uml | C++ |
| --- | --- |
| ```smart_ptr:shared_ptr``` | ```std::shared_ptr``` |
| ```smart_ptr:weak_ptr  ``` | ```std::weak_ptr  ``` |
| ```smart_ptr:unique_ptr``` | ```std::unique_ptr``` |


And in the tab ```C++ [5]``` > External Types:

| External Type | Include etc... |
| --- | --- |
|```std::shared_ptr``` | ```#include <memory>``` |
|```std::weak_ptr```   | ```#include <memory>``` |
|```std::unique_ptr``` | ```#include <memory>``` |
|```smart_ptr:vector_shared``` | ```#include <memory>``` |
|                              | ```#include <vector>``` |
|```smart_ptr:vector_weak```   | ```#include <memory>``` |
|                              | ```#include <vector>``` |




### Use it
Now when you create a relation between classes, you can select stereotypes that will create either:

```c++
std::shared_ptr<T> x;
std::weak_ptr<T> x;
std::unique_ptr<T> x;
std::vector<std::shared_ptr<T> > x;
std::vector<std::weak_ptr<T> > x;
```
Hope you enjoy!

[1]: https://www.bouml.fr/

## License

All the contents of this repository is licensed under the GNU General Public License (GPL)

    Copyright (C) 2018  Jules Waldhart
    This program is free software; you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation; either version 2 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    See the LICENSE file containing a copy of the GNU General Public
    License for more details.
    
[gpl2]:https://www.gnu.org/licenses/old-licenses/gpl-2.0.html
[gpl3]:https://www.gnu.org/copyleft/gpl-3.0.html
