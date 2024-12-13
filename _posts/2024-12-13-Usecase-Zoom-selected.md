---
title: "Use case: Zoom selected element"
date: 2024-11-29T15:34:30-04:00
categories:
  - blog
tags:
  - coding
---

We are going to create  a macro in C# that zooms to a selected element.

![alt text](assets/images/image01.png)

From Revit 2025 Visual Studio Code and .NET SDK 8.0 are pre-requisites for creating macros. 

More information can be found in this article: https://help.autodesk.com/view/RVT/2025/ENU/?guid=GUID-071913D8-214A-45AB-A798-A81653E77F88

From the manage tab let’s open the macro manager and create a new Module. This is a file that will contain all our macros. Give it a name and click ok.

![image.png](https://file.notion.so/f/f/9addda3f-6809-43bd-80aa-fc9f6e5fe54e/26b6d572-ff00-4d57-b6c1-fd2ef3032edd/image.png?table=block&id=1577403c-e188-8017-b04a-ee5a82999afd&spaceId=9addda3f-6809-43bd-80aa-fc9f6e5fe54e&expirationTimestamp=1734220800000&signature=ShajIsr6Ft9-tPYOhjmKkGfIePN3yDRPpRDqZfpLVbI&downloadName=image.png)

VSCode will automatically launch and we can start writing our macro straight away. This a new feature from Revit 2025. If you are using an older version the code will be the same.

There is already an example of a macro commented in green so we can follow that template and write

*public void* and the name of our macro followed by parenthesis and curly brackets.

To test that everything is working we can try showing a dialog box with the classic Hello World. 

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9addda3f-6809-43bd-80aa-fc9f6e5fe54e/28bdb589-5d03-4a30-94cf-98cdceae9e84/image.png)

The first parameter is the title of the window and the second is the message we want to display. Both of them are text parameters (strings) so we need to use quotation marks.

If we go back to Revit, the macro is still not visible under our Module. The reason is we did not “build” it yet. Our code that we write in C# needs to be compiled into machine readable code. 

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9addda3f-6809-43bd-80aa-fc9f6e5fe54e/bbef768b-bdcc-42dd-81b3-a40757dce10d/image.png)

So let’s go back to visual studio code and run our macro using the play button in the top right corner.

In the terminal we see that our macro has now been converted into a .dll file.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9addda3f-6809-43bd-80aa-fc9f6e5fe54e/c59a7146-a2a8-4f62-87cd-118f054c28a1/image.png)

So if we go back in Revit we can now see our macro under the module we created before.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9addda3f-6809-43bd-80aa-fc9f6e5fe54e/26b00ae3-8f80-42de-83a0-530269c13f73/image.png)

If we select the macro and click run it will be executed and we will see our “Hello World” task dialog popping up.

Let’s finish writing our code and proceed to testing it.

When moving our code from Python to C# remember that we need to declare the datatype of each variable.

The method we are going to use to zoom to the selected element is called ShowElements and it belongs to the UIDocument namespace. 

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9addda3f-6809-43bd-80aa-fc9f6e5fe54e/c9fdf083-9bf9-4b79-9291-87fbe67d5e73/image.png)

We can get the UIDocument by using the ActiveUIDocument property of the Application.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9addda3f-6809-43bd-80aa-fc9f6e5fe54e/3fdc2a32-02ff-49ab-bf5a-276a16a9bd4a/image.png)

We are lucky, the code we are writing sits inside an Application class so to access the ActiveUIDocument property we can just write: *this.ActiveUIDocument* or *ActiveUIDocument* whatever makes more sense for you. 

It returns an UIDocument object so we can write:

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9addda3f-6809-43bd-80aa-fc9f6e5fe54e/d5d86f68-b9bc-49e0-b50c-647526ea4e75/image.png)

The other parameter we need is the Element to zoom to. Which in our case is the current selected element.

We can get the selected element again by using another property of the UIDocument. The Selection property has a method called GetElementIds which returns a list of elementids that we can pass to our showelements method.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9addda3f-6809-43bd-80aa-fc9f6e5fe54e/9a2216ab-e047-44c9-955e-97a8333b5162/image.png)

So to access the UIDocument Selection property we can write uidoc,Selection and to access the GetEleemntIds method we add .GetElementIds with open and close parenthesis to denote that we are calling a method.

If we hover the mouse onto GetElementIds, VSCode tells us that this method returns a collection (i.e. a list) of element ids that are currently selected in the project.

So our variable data type will ne an ICollection of ElementId and we can name it selectedElements or whatever if you prefer.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9addda3f-6809-43bd-80aa-fc9f6e5fe54e/fd7069d9-a2f2-40cf-a75e-9ed34c0bcba0/image.png)

Now we have all the inputs required to call the ShowElements method. Firstly the uidoc class where the methods belong to. And secondly the list of elements that we just created.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9addda3f-6809-43bd-80aa-fc9f6e5fe54e/cf995626-d89d-4b20-98ce-eb19783fe5f4/image.png)

Remember to compile the code before switching back to Revit.

In Revit now we can select an element in a view, activate the other view by pressing the middle mouse button, calling the macro manager (it’s faster if we set a keyboard shortcut) and run our macro.

https://help.autodesk.com/view/RVT/2025/ENU/?guid=GUID-468D3029-11FF-4C1D-BBCA-AE1C66C5E028