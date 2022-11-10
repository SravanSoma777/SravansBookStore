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

1632 2022-11-07

-- starting now on part 2, built the project and there were no errors evrything is good. 
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
-- then added migration using the same command



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
-- then implemented a delete method in categoru.js
-- added the delete functionality in category.js with including the onclick event to the delete function
-- Added the delete(url) function code
-- After Adding Everything related to delete when built there is no error and when run there is no errors but when creating a category there is an error
System.NotImplementedException: 'The method or operation is not implemented

-- will work on it later

1739 2022-11-10

--- built the project no errors but there is an exception 
-- And Replaced The given repository.cs file with the current one 