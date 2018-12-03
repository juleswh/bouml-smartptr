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

### Use it
Now when you create a relation between classes, you can select stereotypes that will create either:

<pre>
std::shared_ptr<T> x;
std::weak_ptr<T> x;
std::unique_ptr<T> x;
std::vector<std::shared_ptr<T> > x;
std::vector<std::weak_ptr<T> > x;
</pre>

Hope you enjoy!

[1]: https://www.bouml.fr/
