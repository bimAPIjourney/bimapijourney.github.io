---
title: "Use case: Zoom selected element"
date: 2024-11-29T15:34:30-04:00
categories:
  - blog
tags:
  - coding
---

We are going to create  a macro in C# that zooms to a selected element.

![alt text](/assets/images/zoomSelect/image01.png)

From Revit 2025 Visual Studio Code and .NET SDK 8.0 are pre-requisites for creating macros. 

More information can be found in this article: https://help.autodesk.com/view/RVT/2025/ENU/?guid=GUID-071913D8-214A-45AB-A798-A81653E77F88

From the manage tab let’s open the macro manager and create a new Module. This is a file that will contain all our macros. Give it a name and click ok.

![alt text](/assets/images/zoomSelect/image02.png)

VSCode will automatically launch and we can start writing our macro straight away. This a new feature from Revit 2025. If you are using an older version the code will be the same.

There is already an example of a macro commented in green so we can follow that template and write

*public void* and the name of our macro followed by parenthesis and curly brackets.

To test that everything is working we can try showing a dialog box with the classic Hello World. 

```cs
public void ZoomSelected(){
  TaskDialog.Show("Hello", "Hello World")
}
```

The first parameter is the title of the window and the second is the message we want to display. Both of them are text parameters (strings) so we need to use quotation marks.

If we go back to Revit, the macro is still not visible under our Module. The reason is we did not “build” it yet. Our code that we write in C# needs to be compiled into machine readable code. 

![alt text](/assets/images/zoomSelect/image02.png)

So let’s go back to visual studio code and run our macro using the play button in the top right corner.

In the terminal we see that our macro has now been converted into a .dll file.

![alt text](/assets/images/zoomSelect/image04.png)

So if we go back in Revit we can now see our macro under the module we created before.

![alt text](/assets/images/zoomSelect/image05.png)

If we select the macro and click run it will be executed and we will see our “Hello World” task dialog popping up.

Let’s finish writing our code and proceed to testing it.

When moving our code from Python to C# remember that we need to declare the datatype of each variable.

The method we are going to use to zoom to the selected element is called ShowElements and it belongs to the UIDocument namespace. 

![alt text](/assets/images/zoomSelect/image06.png)

We can get the UIDocument by using the ActiveUIDocument property of the Application.

![alt text](/assets/images/zoomSelect/image07.png)

We are lucky, the code we are writing sits inside an Application class so to access the ActiveUIDocument property we can just write: *this.ActiveUIDocument* or *ActiveUIDocument* whatever makes more sense for you. 

It returns an UIDocument object so we can write:

```cs
UIDocument uidoc = this.ActiveUIDocument;
```

The other parameter we need is the Element to zoom to. Which in our case is the current selected element.

We can get the selected element again by using another property of the UIDocument. The Selection property has a method called GetElementIds which returns a list of elementids that we can pass to our showelements method.

![alt text](/assets/images/zoomSelect/image08.png)

So to access the UIDocument Selection property we can write uidoc,Selection and to access the GetEleemntIds method we add .GetElementIds with open and close parenthesis to denote that we are calling a method.

If we hover the mouse onto GetElementIds, VSCode tells us that this method returns a collection (i.e. a list) of element ids that are currently selected in the project.

So our variable data type will ne an ICollection of ElementId and we can name it selectedElements or whatever if you prefer.

```cs
ICollection<ElementId> selectedElements = uidoc.Selection.GetElementIds();
```

Now we have all the inputs required to call the ShowElements method. Firstly the uidoc class where the methods belong to. And secondly the list of elements that we just created.

```cs
uidoc.ShowElements(selectedElements);
```

Remember to compile the code before switching back to Revit.

In Revit now we can select an element in a view, activate the other view by pressing the middle mouse button, calling the macro manager (it’s faster if we set a keyboard shortcut) and run our macro.

https://help.autodesk.com/view/RVT/2025/ENU/?guid=GUID-468D3029-11FF-4C1D-BBCA-AE1C66C5E028