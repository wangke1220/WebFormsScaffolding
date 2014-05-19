ASP.NET Web Forms Scaffolding
===================

 -- [View the ASP.NET Web Forms Scaffolder at the Visual Studio Gallery](http://visualstudiogallery.msdn.microsoft.com/a6c3614f-83be-4749-afbc-8da394b6ea86) --

_Scaffolding for Web Forms in Visual Studio 2013_. Given a model class, the Web Forms Scaffolder generates List, Insert, Edit, and Delete pages. The Web Forms Scaffolder uses the Entity Framework, Twitter Bootstrap, and Dynamic Data.

![Insert Movie](/READMEImages/InsertMovie.png "Insert Movie")

## Installing the Web Forms Scaffolder

The Web Forms Scaffolder requires Visual Studio 2013 _Update 2_. It supports both C# and Visual Basic .NET.

You can install the Web Forms Scaffolder directly from within Visual Studio. Select the menu option Tools, Extensions and Updates, and install the Web Forms Scaffolder.

![Install Web Forms Scaffolder](/READMEImages/Install.png "Install Web Forms Scaffolder")

## Using the Web Forms Scaffolder

First, you need to create the model class that you want to scaffold. For example, here is a simple Movie class:

```C#
public class Movie
{
    public int Id { get; set; }

    [Required(ErrorMessage="Movie title is required.")]
    public string Title { get; set; }

    [Required(ErrorMessage="Movie director is required.")]
    public string Director { get; set; }

    [DataType(DataType.MultilineText)]
    public string Comments { get; set; }

    public int Count { get; set; }

    public decimal Price { get; set; }

    [Display(Name="Release Date")]
    public DateTime ReleaseDate { get; set; }
}

```

Next, right-click in the Solution Explorer window and select Add, New Scaffolded Item. From the Add Scaffold dialog, select the Web Forms Scaffolder and click the Add button.

![Add New Scaffolded Item](/READMEImages/AddNewScaffoldedItem.png "Add, New Scaffolded Item")

Use the Add Web Forms Pages dialog to set several important options for the scaffolder. Select a model class, an Entity Framework data context, and a Master Page.

![Add Web Forms Pages Dialog](/READMEImages/AddWebFormsPages.png "Add Web Forms Pages Dialog")

After you click the Add button, the Web Forms Scaffolder adds a new folder that contains Default.aspx, Delete.aspx, Edit.aspx, and Insert.aspx pages. The Web Forms Scaffolder also creates a DynamicData folder that contains Field templates. Finally, the Scaffolder
creates a GenericRepository class in the Models folder that it uses to interact with your database.

## Working with Associated Entities

You can use the Web Forms Scaffolder with entities that have associations. For example, the following Product
class is associated with the Category class:

```C#
public class Product
{
    public int Id { get; set; }

    [Required(ErrorMessage="Product name is required.")]
    public string Name { get; set; }

    public decimal Price { get; set; }

    // The CategoryId property is scaffolded. It's what
    // gets set in the DropDownList.
    [Display(Name="Category")]
    public int CategoryId { get; set; }


    // The Category property is the navigation property.
    // This property is not scaffolded but it creates the 
    // association between products and categories.
    public Category Category { get; set; }
}


public class Category
{
    public int Id { get; set; }

    [Display]  // Use the display attribute to indicate the data text field for the DropDownList
    public string Name { get; set; }
}

```

The Product class has two properties that associate the Product class with the Category class: the Category property and the CategoryId property.
The Category property creates the association between Products and Categories. This property is not scaffolded by the Web Forms scaffolder but it is required to establish the association.

The CategoryId property, on the other hand, is scaffolded. Notice that you can use the [Display] attribute to provide a friendly name for the property when it is displayed.

When the CategoryId property is scaffolded, a DropDownList appears that enables you to select the associated category. This DropDownList appears in both the Insert.aspx and Edit.aspx forms.

![Associated Entities](/READMEImages/Associations.png "Associations")

## Working with Enumerations
You can use the Web Forms Scaffolder to scaffold properties that have enumerations for their values. For example, 
the following Employee model uses enumerations for its SalaryLevel and Region properties.

```C#
public class Employee
{
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    public Guid Id { get; set; }

    [Required]
    [DataType(DataType.EmailAddress)]
    public string Email { get; set; }

    [DataType(DataType.Url)]
    [Display(Name="Home Page URL:")]
    public string HomePage { get; set; }

    [Required(ErrorMessage="You must enter a salary level")]
    public SalaryLevel Salary { get; set; }

    // selecting a region is optional
    public Region? Region { get; set; }
}

public enum SalaryLevel
{
    Level1,
    Level2,
    Level3
}

public enum Region
{
    West,
    Central,
    East,
    Hawaii
}

```
Notice that the Region property is optional.

Here's what the Insert page generated by the Scaffolder looks like.

![Enumerations](/READMEImages/Enumerations.png "Enumerations")

## Customizing the Generated Content

The Web Forms Scaffolder uses Dynamic Data templates. If you want to customize the appearance of the pages generated by the Scaffolder then you can modify the Dynamic Data Field templates. Learn more about Dynamic Data at http://msdn.microsoft.com/en-us/library/cc488545.aspx  

The Web Forms Scaffolder takes advantage of Twitter Bootstrap for styling the pages. You aren't required to use Twitter Bootstrap with the Web Forms Scaffolder. However, if you don't use Twitter Bootstrap then you are responsible for creating your own Cascading Style Sheet. Learn more about Twitter Bootstrap at http://getbootstrap.com/   

## Samples

This	 GitHub project includes a Visual Studio Project named Samples that contains three samples of the generated
content from the Web Forms Scaffolder:

* 1_Simple - Contains sample generated content for a simple Movie class.

* 2_Validation - Contains sample generated content for a Book class that uses validation attributes and the IValidatableObject interface.

* 3_Associations - Contains sample generated content for an associated Product and Category class.