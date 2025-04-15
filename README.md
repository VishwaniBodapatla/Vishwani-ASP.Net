**Project Setup: EF Core + Scaffolding Instructions**
This project uses Entity Framework Core for database access. Below are the steps to install EF Core packages and scaffold the database using an existing .sql script hosted in another repository.

**SQL Script Reference**
You can find the full database schema and data in this separate GitHub repository:
https://github.com/VishwaniBodapatla/Vishwani-ASP.Net/blob/main/scripts_OrganicDB_V1.sql

**Step 1: Install EF Core CLI Tools**
If you haven't already, install the EF Core CLI:


dotnet tool install --global dotnet-ef

Run dotnet ef to verify it's installed correctly.

**Step 2: Install Required EF Core NuGet Packages**
Install the necessary EF Core packages for your database provider (e.g., SQL Server):

dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Design
💡 If you're using another database (e.g., PostgreSQL or SQLite), install the relevant provider instead.

 **Step 3: Scaffold the Database Context and Models**
Make sure your database is restored using the .sql file from the linked repo. Once it's available locally, use EF Core's reverse engineering to scaffold the models.

dotnet ef dbcontext scaffold "Server=YOUR_SERVER;Database=YOUR_DATABASE;Trusted_Connection=True;" Microsoft.EntityFrameworkCore.SqlServer -o Models -f
🔧 Replace:
YOUR_SERVER with your SQL Server name (e.g., localhost, .\SQLEXPRESS, etc.)

YOUR_DATABASE with the name of your restored database

**Step 4: Project Structure**
After scaffolding, your project will have:

/Models
  ├── YourDbContext.cs
  └── AllEntityModels.cs

**Step 5: Run the Project**
Make sure to configure your DbContext in Startup.cs or Program.cs like this:

services.AddDbContext<YourDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    
Also, ensure your appsettings.json contains:


"ConnectionStrings": {
  "DefaultConnection": "Server=YOUR_SERVER;Database=YOUR_DATABASE;Trusted_Connection=True;"
}




1.	Home Page
Note: Since you are not yet logged in, you don’t see add to card option on items.
![image](https://github.com/user-attachments/assets/ba5f8c22-9c3c-4c6c-b745-8d0bb4044aa9)

 
3.	Login Page

Click on Login on the right side of the home page to Login. If you are not registered yet, you can register first. 
![image](https://github.com/user-attachments/assets/aa4eb167-29e4-49c2-87c1-c2c78824cf5d)


 
3.	Registration Page
Once you are registered, you will be redirected to home page. Now you can login using your Username and Password.
 
![image](https://github.com/user-attachments/assets/d3da9036-687e-486d-b5f9-494531c3f9a1)

4.	Shopping Page
Once you log in you can view products/items along with “Add to cart option” and can choose quantity. You can click on “Add to cart” to add your items to cart.
![image](https://github.com/user-attachments/assets/ab384ee7-abdf-42ed-8fa0-c1c7533d1a05)

 
6.	Cart Page
To view all items you choose, click on Your Cart where you can view all the items along with calculated price. 
Here you can either choose to “Check Out” (at the end of page) or reduce and increase quantity  or remove the products entirely or continue shopping (Click on Continue Shopping button).
![image](https://github.com/user-attachments/assets/4774f7ef-1936-45fb-a106-3bf6d580ab59)

 
8.	Check Out Page
Click on place order to place order or cancel the order.

 ![image](https://github.com/user-attachments/assets/97ff681d-4bc7-4370-9005-4f3814771390)




Inventory Management


Adding/ removing/ editing the Product or items (CRUD)
Note: All Products page is visible to the public now, but it should only be visible to admin. This is my next step.
https://localhost:44308/Products/List
This page redirects you to the page with a list of products. 
Click on Add product to add a product. 
![image](https://github.com/user-attachments/assets/63e3ad46-fbd8-4f95-b7d4-60ede98de778)

 


Add the product details like name, stock quantity (available in store), packaging unit determines, quantity of each unit and you can add the nutrient details and mention which part of diet, the items belong to. This information is for the next steps of the project.
![image](https://github.com/user-attachments/assets/4549ae37-3d05-4535-9d2d-8c87a82ac60b)


 

You can edit as well as remove the object.

