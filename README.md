ASP.NET Web Forms Scaffolding
===================

Scaffolding for Web Forms in Visual Studio 2013. Given a model class, the Web Forms Scaffolder generates a List, Insert, Edit, and Delete page. The Web Forms Scaffolder uses the Entity Framework, Twitter Bootstrap, and Dynamic Data.

# Installing the Web Forms Scaffolder

You can install the Web Forms Scaffolder directly from within Visual Studio. Select the menu option Tools, Extensions and Updates, and install the Web Forms Scaffolder.


# Using the Web Forms Scaffolder

First, you need to create the model class that you want to scaffold. For example, here is a simple Movie class:

```C#
public class Movie
{
    public int Id { get; set; }

    public string Title { get; set; }

    public string Director { get; set; }
}

```

Next, right-click in the Solution Explorer window and select Add, New Scaffolded Item. From the Add Scaffold dialog, select the Web Forms Scaffolder and click the Add button.


Use the Web Forms Scaffolder dialog to set several important options for the scaffolder. Select a model class, an Entity Framework data context, and a Master Page.


After you click 


# Customizing the Generated Content

The Web Forms Scaffolder uses Dynamic Data templates. If you want to customize the appearance of the pages generated by the Scaffolder then you can modify the Dynamic Data Entity templates and Field templates.  
