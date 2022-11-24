0930 2022-11-02

--- Created a new Asp.net Core Web Application version 5.0 With
-  Individual Accounts Authentication
-  Configure for HTTPS Enabled
-  Enabled Razor Runtime Compilation


0946 2022-11-02

-- Reviewed All the mvc files
-- In the Startup.cs file Left the DefaultIndentity Blank

1002 2022-11-02

-- Set breakpoints in the Homecontroller.cs file at the index and privacy action methods and 
	browser directly closed, so i had to continue for the site to proceed
-- Everything Worked Well Until now Onto the next one

1012 2022-11-02

- Went to the Bootstrap.com and selected a theme called Vapor and Downloaded it
- Replaced the Downloaded file with the original bootstrap.css file in the lib => bootstrap => dist => css
- In the Views =>Shared =>_Layout.cshtml changed the linked file name from bootstrap.min.css to the file downloaded bootstrap.css
- Changed the nav class from navbar-light-->Navbar-dark
- Changed bg-white-->bg-primary
- Removed 'Text-dark' refrences from _loyout.cshtml
- Added text-white-50 and bg-primary properties to the footer class.
- In _loginPartial.cshtml removed all the references to the 'text-dark'.
- Ran the Project and changes were seen with the bootstrap theme and the links change colors.

1025 2022-11-02

-- Added the Additional Script and Stylesheets given to the _Layout.cshtml file
-- Added a Dropdown to the nav in the _Layout.cshtml
-- Renamed the Dropdown name to content management

1032 2022-11-02

-- Added three new .NET core class library Projects naming:
					=> SravansBooks.DataAccess
					=> SravansBooks.Models
					=> SravansBooks.Utility
-- Copied and Pasted the Data folder from the original project to the DataAccess Project and deleted it from the original
-- Installed given packages using manage NuGet packages in the project. the packages are:
				=> Microsoft.EntityFrameworkCore.Relational
				=> Microsoft.EntityFrameworkCore.SqlServer
			VERSION = "5.0.11".
-- Deleted the Migrations folder
-- Installed Another NuGet Package => Microsoft.AspNetCore.Identity.EntityFrameworkCore(5.0.11)
-- Modified the namespace from SravansBookStore.Data => SravansBookStore.DataAccess.Data
-- Deleted all the class files named class1 generated with the library project

1115 2022-11-02

-- Copied and Pasted the Models folder from the original project to the Models Project and deleted it from the original
-- Modified Error.cshtml to the reference
-- Added project reference to the main project with the dataAccess and Model projects 
-- Renamed Models Folder to ViewModels.
-- And Changed ErrorViewModel.cs File's Namespace from SravansBookStore.Models => SravansBookStore.Models.ViewModels
-- Modified Using Statement from using SravansBookStore.Data; => using SravansBookStore.DataAccess.Data; and applicationDbContext Error was gone.
-- In Error.cshtml file modified Reference to be SravansBookStore.Models.ViewModels.ErrorViewModels
--- All the Errors Were Resolved 
-- Added A Static Details Class file to the Utility Project and named it 'SD.cs'.
-- Modified the Properties of the class to Public Static
-- Added the Utility Projects Reference to the main project And 
-- Added project references to Models and Utility in the DataAccess Project


0100 2022-11-02

-- Added An Area Called Customers in Areas
-- Changed the Routing of the Startup.cs File As given in the ScaffoldingREADME.
-- Moved the HomeController.cs to the Area=>Customer=>Controller Folder and deleted
-- Added this line [Area("Customers")] to the HomeController.cs file before the class in the namespace to explicitly define that Controller is in the Controller Area
-- Moved View=>Home Folder to the Customer/Views Folder
-- and Ran it Everything is gone Its just palin html
-- Copied the _ViewImport and _ViewStart to customer Area
-- Modified The _viewStart.cshtml Path to Layout = "~/Views/Shared/_Layout.cshtml"; And Ran the Application and all the styles were back

0210 2022-11-02

-- Added a new Admin Area to the Areas
-- Added the View Files As shown in the tutorial to the Admin view folder 
-- And Deleted Data and Models Folder
-- Deleted the Main Projects Controller folder as it was empty
-- Updated the Github Repository and commited with the Instructions given

======================================================================================
1111 2022-11-03

-- In the startup.cs file At line 45 used  in the configure method app.UseDatabaseErrorPage();
and changed it with app.UseMigrationsEndPoint(); and that seems to have resolved the problem


0550 2022-11-06

-- As told Changed the Target framework from 5.0 to .netcore 3.1 and updated all their dependency packages. 
==============================================================================================

1632 2022-11-07 Starting PART 02

-- starting now on part 2, built the project and there were no errors everything is good.
-- in appsettings.json changed my database connection "Server=(localdb)\\mssqllocaldb;/////Database=SravansBookStore////;Trusted_Connection=True;MultipleActiveResultSets=true"
-- Used this Command create migration using Package Manager Console
			-add-migration AddDefaultIdentityMigration
			file name == 20221107214316_AddDefaultIdentityMigration.cs =>20221107214316_AddDefaultIdentityMigration.Designer.cs
-- and updated database " update-database"
-- created a new class file in models project and gave some properties
-- added migration using this command in package manager console add-migration AddCategoryToDb
-- Created migration file name is 20221107221342_AddCategoryToDb.cs => 20221107221342_AddCategoryToDb.Designer.cs
-- the new migration file was empty
-- in dataAccesss.data => application.dbcontext.cs added public DbSet<Category> Categories { get; set; } 
-- then Removed migrations done previously to avoid duplication
-- then added migration using the same command add-migration AddCategoryToDb



1749 2022-11-07

-- Added A new folder in the DataAccess project naming it Repository and then created a new folder inside it called IRepository 
-- Created an interface item called IRepository.cs
-- Modified interface to use methods for CRUD
		-Get item from the Db
		-List of categories
		-Add Objects
		-Remove Objects

1816 2022-11-07

-- Created a class file that implements the repository
-- and modified the code to create the constructors and dependency injection

1839 2022-11-07

-- created individual repository for category and all potential models for the fututre
		-- Categoryrepository.cs
		and interface file ICategroyInterface.cs 

-- Modified CategoryRepository.cs file with the using statements and methods pointing to ApplicationDbContext
-- Modified ICategoryRepository interface with a update void method
-- and updated the void method to retreive the first or default category object and pass the id as the generic entity which matches the category id


1938 2022-11-07

-- implemented a stored repository and map multiple repositories in a unit of work
-- added a new interface in the IRespository folder called ISP_Call.cs that extends IDisposable
-- Installed a nuget package called Dapper
-- and included the methods shown in the the given file
-- Added a new class in the repository folder called SP_Call.cs 
-- added using statements and implemented interface ISP_Call
-- Added A DB connection and updated using statements 


2100 2022-11-07

--Added a new interface to the IRespository folder called IUnitOfWork.cs and Updated it to be public and its code.
-- Added a new class in Repository Folder called UnitofWork.cs and modified the code 
-- And implemented the class with the interface 
-- and in startup.cs file in the configureServices method addedthe following lines to make accessible by the project
        --services.AddScoped<IUnitOfWork, UnitOfWork>();

-- Built the project, there were no errors everything is fine and running smooth.


=========================================================================
1032 2022-11-08

-- Started Again with the project 2.3 Category CRUD
-- controller folder didn't have support for previewing so had to delete the folder and add a new one with the same name
-- Added a new mvc controller-empty named CategoryController.cs in the controllers folder
-- Modified the code to use the IunitOfWork from the .DataAccess project and the IRepository Folder
-- Added  a Category folder in the Admin/Views folder and created a new view called index.cshtml and modified with the code given.
-- and added a link to access this index file from the layout and put the link in the dropdown rather than nav


1150 2022-11-08
-- Added a new item category.js and added return type code for the icons 
-- in Index.cshtml with @setion Scripts use called the js file created 
-- Added IActionResult code to the controller and Added a view and  added html to the new view 
-- Created a partial view  in the general views/Shared folder called _CreateAndBackToList.cshtml and added the required code
-- created another partial view for the EDIT| BACK in the same genral views/shared folder called _EditAndBackToListButton and
Added the required code and addditonal @model razor statement too

/////////*********************************************
Errors exceptions to be handled
---- System.NotImplementedException: 'The method or operation is not implemented
----An exception of type 'System.NotImplementedException' occurred in SravansBooks.DataAccess.dll but was not handled in user code
The method or operation is not implemented.

--Exception thrown while trying to create and update the category


1520 2022-11-08

--- tried to solve the exception for creating and updating but it doesnt show keeps on getting exception 
-- went on and added HttpDelete API call in the categoryController.cs
-- then implemented a delete method in category.js
-- added the delete functionality in category.js with including the onclick event to the delete function
-- Added the delete(url) function code
-- After Adding Everything related to delete when built there is no error and when run there is no errors but when creating a category there is an error
System.NotImplementedException: 'The method or operation is not implemented

-- will work on it later

1739 2022-11-10

--- built the project no errors but there is an exception 
-- And Replaced The given repository.cs file with the current one 
-- Not Able to create a new category dont know why should look into it an dont have any errors
just redirects to index page and does nothing.


2131 2022-11-13

-- in CategoryController.cs the HttpGet and HttpDelete API Calls did not get committed so had to do it again
-- Dont Know Whats happening, not able to create a Category and when clicked Create it redirects to index 
and the category is not shown Working on it


2022-11-14 1756

-- Made some changes in UntiOFWork.cs file took out the void IUnitOfWork.Save(); method
-- Changed src attritube from  <script src="/js/category.js"></script> to <script src="~/js/category.js"></script>
-- In Upsert.cshtml file changed method from POST to post.
-- Updated Category.js file on line 10 there was a spelling mistake "reder": function (data) { to  "render": function (data) {
-- Built the project, there were no erorrs
-- Created a Category successfully as directed, Updated it and deleted. Everything Works.

////////////////////////////////////////////////////////////////////////////////

Starting With PART 03
////////////

2022-11-21 1500

-- Working on CoverType CRUD
-- Created a CoverType.cs class file in models folder
-- And delcared ID and Name properties same as the Category.cs properties
-- Added CoverTypeRepository.cs class file to Repository folder
-- Added ICoverTypeRepository.cs interface file to IRepository folder
-- Added CoverType to IunitOfWork.cs Interface file ** ICoverTypeRepository CoverType { get; } **
-- Implemented Interface and *** public ICoverTypeRepository CoverType { get; private set;} *** got generated
-- In Data/ApplicationDbContext.cs added reference to CoverTypes using ****** public DbSet<CoverType> CoverTypes { get; set; }****
-- And created migration using PMC with Command /////
						add-migration AddCoverTypeToDb
------ The generated migration file name with timestamp/////// 20221121212703_AddCoverTypeToDb.cs
						and designer migration file name////// 20221121212703_AddCoverTypeToDb.Designer.cs
-- And Updated Database

2022-11-21 1800

-- Added CoverType to navbar in file _layout.cshtml
-- Added a new controller for CoverType called CoverTypeController
-- Created a folder in Areas/Admin/Views called CoverType to add Index and Upsert view files
-- Created a new view file called Index.cshtml to use DataTables and Copied the content from category/index file and edited it to match CoverType
-- Created a new view file called Upset.cshtml to Create and Update DataTables of the Covertype
-- created new JavaScript file called CoverType.js to retrieve the information of the datatables and display and Copied the javascript file of category and made changes to run with coverType
-- made some changes in the bootstrap.css file to comply with the user experience 
-- Added upsert, HttpGet, Httppost and API calls to the CoverTypeController file

2022-11-21 1930 

-- Working on Product CRUD 
-- Added a new class file called Product.cs in the models folder
-- Added Properties given in the file and made the class public
-- Added Reference in the ApplicationDbContext.cs ///   public DbSet<Product> Products { get; set; }
-- created migration using PMC with Command ////
						add-migration AddProductToDb
-- And Generated migration file name with timestamp ///// 20221122011530_AddProductToDb.cs
								and designer filename///// 20221122011530_AddProductToDb.Designer.cs
-- And Updated Database
-- Reviewed the newly created Products table in the SQL Server Object Explorer
-- Updated the Product.cs file with Validations as follows
							- Made Title Required
							- Made ISBN Required
							- Made Author Required
-- And Created a Migration using PMC with command////
						add-migration AddValidationToDb 
-- And Generated Migration filename with Timestamp ///// 20221122012015_AddValidaionToDb.cs
						and designer migration file name/// 20221122012015_AddValidaionToDb.Designer.cs
--And Updated database PMC Command update-database


===========
2022-11-21 2000

-- Added Product to the Repository by
	-Adding Interface called IProductRepository to IRepository
	-Adding class file called ProductReposiotry to Repository folder and implemented the Interface  
		and made Modifications given to the Update method in the ProductRepository.cs file
	-Adding Product to the IUnitOfWork // IProductRepository Product { get; }
	-And Implementing the IunitOfWork Interface generated  //public IProductRepository Product { get; private set; }
-- Built and Checked, there were no errors

============
2022-11-21 2030

-- Added ProductController.cs in Areas/Admin/Controllers folder to perform CRUD operations
-- Added the IWebHostEnvironment call and added using statement AspNetCore.Hosting for it to work
-- Created a View Model in the models folder to hold the product object called ProductVM.cs and created select list for Category and CoverType
-- Modified the ProductVM to be public and Installed the Microsoft.AspNetCore.Mvc.ViewFeatures package
-- Modifed the ProductController so the IActionResult Upsert calls to the ProductVM and included the using statement to viewModels folder and Microsoft.AspNetCore.Rendering
-- Commented the Upsert Post method
-- Modified the API call to include Category and CoverType properties
-- Added an index view file in the Areas/Admin/Views/Product folder called Index.cshtml
-- Copied and pasted the index file of the Category and made modificaions to run for the Product
-- Created a new product.js file to use Datatables
-- Copied and pasted the category.js file in the Product.js file and made modifications like url and columns to run for the Product
-- Modified the _layout.cshtml to add new link to the Product in the DropDown
-- Built and checked, no Build Erorrs
-- Ran the Application 
-- there is an sql error but the slide said it was okay and we were going to solve maybe in the next slide 


===========
2022-11-21 2130


-- Created a view file named  Upsert.cshtml in the Product views folder
-- And Modified the Upsert file with the given Upsert file from the Assignmetnnt 2 files
-- Added a rich textBox inside Product with tiny.cloud using the API and added a function validateInput() and if empty, displays a sweet alert
				 <script>
						tinymce.init({
							selector: 'textarea',
							plugins: 'lists',
							menubar: 'file edit format'
						});
						function validateInput() {
							if (document.getElementById("uploadBox").value == "") {
								swal("Error", "Please select an image", "error");
								return false;
							}
							return true;
						}
						<script src="https://cdn.tiny.cloud/1/n94ifuzvl80pchikopiwgz2esrw8n28dwcywvpejlqrregfp/tinymce/5/tinymce.min.js">
				 </script>

-- Built the Application there were no errors
-- Ran the application
-- When selected create new product form appeared to create product but not able create it actually. where is goes to the Repository file and return query.ToList(); is empty
-- Added a new folder in wwwrooot folder called images and a subfolder to the images called Products
-- In the productController Uncommented the method post upsert  and modifed the ProductController with the given file
-- Built and checked for erorrs, there were no errors 
-- Ran the Application to create a Product, filled everything and it didnt let me create a product and threw a user handled exception saying that the path given is wrong or not found/
-- and one more thing was that the category list and CoverType Dropdown list were showing the same list as Category so had to change the Dropdown list to CoverTypeList and CoverTypeId for the coverType to be shown 
				/////////System.IO.DirectoryNotFoundException: 'Could not find a part of the path 'C:\images\products\536f7c52-9abb-4e08-875b-9a3dbaafa793.jpg'.'
--///////// then Had to create a new file in the c:// local path of the computer called images/Products and place the image in there
-- So, it made me add the category but there is no sign of picture added, cant see the picture anywhere in the table and if no picture is selected while adding the product there is a warning


