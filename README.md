# AdventureWorks SSDT Demo  
**Repository:** https://github.com/SoumyadeepDatta/AdventureWorks-SSDT-demo.git

This repository contains the **database schema** of the AdventureWorks sample database in a SQL Server Database Project using SQL Server Data Tools (SSDT). It demonstrates:

- Restoring a database from backup  
- Importing the database schema into an SSDT project  
- Version-controlling the schema with Git  
- Generating migration (deployment) scripts  
- Deploying schema to another SQL Server instance

---

## 🚀 Prerequisites

Before you begin, install:

1. **SQL Server** (Developer or Express edition)  
2. **SQL Server Management Studio (SSMS)**  
3. **Microsoft Visual Studio**  
4. **SQL Server Data Tools (SSDT)** extension in Visual Studio  
5. AdventureWorks `.bak` backup file (downloaded from Microsoft samples) :contentReference[oaicite:0]{index=0}

---

## 1️⃣ Restore AdventureWorks in SSMS

1. Open **SQL Server Management Studio** and connect to your SQL Server instance.  
2. Right-click **Databases → Restore Database…**.  
3. Select **Device → Browse…** and choose the AdventureWorks `.bak` file.  
4. Click **OK** to restore the database.  
5. Once restored, you should see `AdventureWorks` under your Databases list.

---

## 2️⃣ Create an SSDT Database Project

1. Open **Visual Studio**.  
2. Click **Create a new project**.  
3. Search for **SQL Server Database Project**.  
4. Name the project `AdventureWorks-SSDT-demo`. 
5. Click **Create**.

---

## 3️⃣ Import Database Schema

1. In Solution Explorer, right-click the project → **Import → Database**.  
2. Connect to your SQL Server instance and select the `AdventureWorks` database.  
3. Click **Start**.  
4. Visual Studio generates schema files for each object and creates folders accordingly.

Typical folder structure:

```
\
|   .gitattributes
|   .gitignore
|   AdventureWorks-SSDT-demo.slnx
|   README.md
|   structure.txt
|   
\---AdventureWorks-SSDT-demo
    |   AdventureWorks-SSDT-demo.dbmdl
    |   AdventureWorks-SSDT-demo.jfm
    |   AdventureWorks-SSDT-demo.sqlproj
    |   AdventureWorks-SSDT-demo.sqlproj.user
    |   ExtendedProperties.sql
    |   FullTextIndexes.sql
    |   
    +---bin
    |   \---Debug
    |           AdventureWorks-SSDT-demo.dacpac
    |           AdventureWorks_SSDT_demo.dll
    |           AdventureWorks_SSDT_demo.pdb
    |           
    +---Database Triggers
    |       ddlDatabaseTriggerLog.sql
    |       
    +---dbo
    |   +---Functions
    |   |       ufnGetAccountingEndDate.sql
    |   |       ufnGetAccountingStartDate.sql
    |   |       ufnGetContactInformation.sql
    |   |       ufnGetDocumentStatusText.sql
    |   |       ufnGetProductDealerPrice.sql
    |   |       ufnGetProductListPrice.sql
    |   |       ufnGetProductStandardCost.sql
    |   |       ufnGetPurchaseOrderStatusText.sql
    |   |       ufnGetSalesOrderStatusText.sql
    |   |       ufnGetStock.sql
    |   |       ufnLeadingZeros.sql
    |   |       
    |   +---Stored Procedures
    |   |       uspGetBillOfMaterials.sql
    |   |       uspGetEmployeeManagers.sql
    |   |       uspGetManagerEmployees.sql
    |   |       uspGetWhereUsedProductID.sql
    |   |       uspLogError.sql
    |   |       uspPrintError.sql
    |   |       uspSearchCandidateResumes.sql
    |   |       
    |   +---Tables
    |   |       AWBuildVersion.sql
    |   |       DatabaseLog.sql
    |   |       ErrorLog.sql
    |   |       
    |   \---User Defined Types
    |           AccountNumber.sql
    |           Flag.sql
    |           Name.sql
    |           NameStyle.sql
    |           OrderNumber.sql
    |           Phone.sql
    |           
    +---HumanResources
    |   +---Stored Procedures
    |   |       uspUpdateEmployeeHireInfo.sql
    |   |       uspUpdateEmployeeLogin.sql
    |   |       uspUpdateEmployeePersonalInfo.sql
    |   |       
    |   +---Tables
    |   |       Department.sql
    |   |       Employee.sql
    |   |       EmployeeDepartmentHistory.sql
    |   |       EmployeePayHistory.sql
    |   |       JobCandidate.sql
    |   |       Shift.sql
    |   |       
    |   +---Views
    |   |       vEmployee.sql
    |   |       vEmployeeDepartment.sql
    |   |       vEmployeeDepartmentHistory.sql
    |   |       vJobCandidate.sql
    |   |       vJobCandidateEducation.sql
    |   |       vJobCandidateEmployment.sql
    |   |       
    |   \---XMLSchemaCollections
    |           HRResumeSchemaCollection.sql
    |           
    +---Import Schema Logs
    |       AdventureWorks-SSDT-_20260225111308.log
    |       
    +---obj
    |   \---Debug
    |           AdventureWorks-SSDT-demo.sqlproj.AssemblyReference.cache
    |           AdventureWorks-SSDT-demo.sqlproj.FileListAbsolute.txt
    |           AdventureWorks_SSDT_demo.dll
    |           AdventureWorks_SSDT_demo.pdb
    |           
    +---Person
    |   +---Tables
    |   |       Address.sql
    |   |       AddressType.sql
    |   |       BusinessEntity.sql
    |   |       BusinessEntityAddress.sql
    |   |       BusinessEntityContact.sql
    |   |       ContactType.sql
    |   |       CountryRegion.sql
    |   |       EmailAddress.sql
    |   |       Password.sql
    |   |       Person.sql
    |   |       PersonPhone.sql
    |   |       PhoneNumberType.sql
    |   |       StateProvince.sql
    |   |       
    |   +---Views
    |   |       vAdditionalContactInfo.sql
    |   |       vStateProvinceCountryRegion.sql
    |   |       
    |   \---XMLSchemaCollections
    |           AdditionalContactInfoSchemaCollection.sql
    |           IndividualSurveySchemaCollection.sql
    |           
    +---Production
    |   +---Tables
    |   |       BillOfMaterials.sql
    |   |       Culture.sql
    |   |       Document.sql
    |   |       Illustration.sql
    |   |       Location.sql
    |   |       Product.sql
    |   |       ProductCategory.sql
    |   |       ProductCostHistory.sql
    |   |       ProductDescription.sql
    |   |       ProductDocument.sql
    |   |       ProductInventory.sql
    |   |       ProductListPriceHistory.sql
    |   |       ProductModel.sql
    |   |       ProductModelIllustration.sql
    |   |       ProductModelProductDescriptionCulture.sql
    |   |       ProductPhoto.sql
    |   |       ProductProductPhoto.sql
    |   |       ProductReview.sql
    |   |       ProductSubcategory.sql
    |   |       ScrapReason.sql
    |   |       TransactionHistory.sql
    |   |       TransactionHistoryArchive.sql
    |   |       UnitMeasure.sql
    |   |       WorkOrder.sql
    |   |       WorkOrderRouting.sql
    |   |       
    |   +---Views
    |   |       vProductAndDescription.sql
    |   |       vProductModelCatalogDescription.sql
    |   |       vProductModelInstructions.sql
    |   |       
    |   \---XMLSchemaCollections
    |           ManuInstructionsSchemaCollection.sql
    |           ProductDescriptionSchemaCollection.sql
    |           
    +---Purchasing
    |   +---Tables
    |   |       ProductVendor.sql
    |   |       PurchaseOrderDetail.sql
    |   |       PurchaseOrderHeader.sql
    |   |       ShipMethod.sql
    |   |       Vendor.sql
    |   |       
    |   \---Views
    |           vVendorWithAddresses.sql
    |           vVendorWithContacts.sql
    |           
    +---Sales
    |   +---Tables
    |   |       CountryRegionCurrency.sql
    |   |       CreditCard.sql
    |   |       Currency.sql
    |   |       CurrencyRate.sql
    |   |       Customer.sql
    |   |       PersonCreditCard.sql
    |   |       SalesOrderDetail.sql
    |   |       SalesOrderHeader.sql
    |   |       SalesOrderHeaderSalesReason.sql
    |   |       SalesPerson.sql
    |   |       SalesPersonQuotaHistory.sql
    |   |       SalesReason.sql
    |   |       SalesTaxRate.sql
    |   |       SalesTerritory.sql
    |   |       SalesTerritoryHistory.sql
    |   |       ShoppingCartItem.sql
    |   |       SpecialOffer.sql
    |   |       SpecialOfferProduct.sql
    |   |       Store.sql
    |   |       
    |   +---Views
    |   |       vIndividualCustomer.sql
    |   |       vPersonDemographics.sql
    |   |       vSalesPerson.sql
    |   |       vSalesPersonSalesByFiscalYears.sql
    |   |       vStoreWithAddresses.sql
    |   |       vStoreWithContacts.sql
    |   |       vStoreWithDemographics.sql
    |   |       
    |   \---XMLSchemaCollections
    |           StoreSurveySchemaCollection.sql
    |           
    +---Security
    |       HumanResources.sql
    |       Person.sql
    |       Production.sql
    |       Purchasing.sql
    |       Sales.sql
    |       
    \---Storage
            AW2025FullTextCatalog.sql
```

---

## 4️⃣ Build the Project

Right-click the project → **Build**.  
A DACPAC is produced at:

```
bin/Debug/AdventureWorks.Database.dacpac
```

This DACPAC contains the full schema model as interpreted by SSDT.

---

## 5️⃣ Version Control (Already Added)

This repository already contains your SSDT project. If you were doing it manually:

```bash
git init
git add .
git commit -m "Initial import of AdventureWorks schema"
git branch -M main
git remote add origin https://github.com/SoumyadeepDatta/AdventureWorks-SSDT-demo.git
git push -u origin main
```

---

## 6️⃣ Generate Migration Scripts

To generate a script that shows schema changes:

1. Right-click the project → **Publish**.  
2. Click **Edit** → set a target database.  
3. Click **Advanced** → choose **Generate Script**.  
4. Click **Generate Script**.

A script file is created with the differences between the project and target.

---

## 7️⃣ Deploy Schema to a New Database

1. Right-click project → **Publish**.  
2. Set target server & new database name (e.g., `AdventureWorks_Clone`).  
3. Click **Publish**.

Visual Studio applies the necessary CREATE/ALTER statements to match the project schema.

---

## 8️⃣ Include Data (Optional)

SSDT projects manage only **schema** by default. To include data:

### 📌 Option A — Generate Data Script in SSMS

1. In SSMS, right-click `AdventureWorks` → **Tasks → Generate Scripts**.  
2. In **Advanced**, set **Types of data to script → Data only**.  
3. Select the option to save it into a single file.  
4. Copy the generated INSERT statements into:

```
Scripts/Post-Deployment/Script.PostDeployment.sql
```

## ✅ How To Create Post-Deployment Script (Correct Way)

### In Visual Studio

1. Right-click the project **AdventureWorks-SSDT-demo**  
   (Make sure you right-click the project, not the solution.)

2. Click:

   Add → Script

3. Choose:

   Post-Deployment Script

4. Click **Add**

---

### What Happens Next?

Visual Studio will automatically create a file named:

PostDeployment.sql

This file is usually created at the **root level of the project** (same level as the `.sqlproj` file).

It will also automatically update the `.sqlproj` file with this entry:

```xml
<PostDeploy Include="PostDeployment.sql" />
```

This line is very important because it tells SSDT to execute the `PostDeployment.sql` file automatically **after schema deployment** during Publish.

---

### Where to Add Data Scripts

Open `PostDeployment.sql` and paste your generated `INSERT` statements (for seed or reference data) into this file.

When you right-click the project and choose **Publish**, SSDT will:

1. Deploy schema (tables, views, procedures, etc.)
2. Then execute `PostDeployment.sql` automatically

⚠ Important: The script runs every time you publish.  
To avoid duplicate data errors, wrap inserts using `IF NOT EXISTS`.

### 📌 Option B — Use a BACPAC

To move schema + data together, export a `.bacpac` from SSMS → **Tasks → Export Data-tier Application**, then import elsewhere.

---

## 🧠 Key Concepts

- SSDT projects store **schema**, not data.  
- DACPAC files encapsulate the current schema model.  
- You can generate migration scripts automatically.  
- Git tracks schema object changes over time.

---

## 🏁 Summary

This repository demonstrates a complete SSDT workflow:

✔ Import database schema  
✔ Version control using Git  
✔ Generate deployment scripts  
✔ Deploy schema to new environments  
✔ Optionally include data via SSMS or data scripts

---

## 🔗 Useful References

- AdventureWorks sample databases download and instructions :contentReference https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver17&tabs=ssms
