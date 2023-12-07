ReadMe.txt for Service Web
Requirements: 
VS 2019 or higher
DevExpress ASP.Net 21.2.5 (Currently)
Access to the SQL server on both GSS2k19SW (Test) and GSS2k19AWSSQL (Live)
Knowledge of MVC
Project Solution is SW_TestCust.sln

Initially you will need to download the latest from http://gss2k19svn3/svn/DevIHP/SWNet_MVC/Trunk
This is the latest and greatest for the live version of the Service Web

Once downloaded you will need to grab the web.config (currently from someone on the House Projects team that works on the Service Web regularly)
This will need to be placed in the main folder of the project, it will be needed to run.

Running the Application
Make sure that the following items have been set (You can also use Edge instead of Chrome)

 

We use MVC with javascript, JQuery, and HTML

NuGet Packages Used (In addition to normal ones)
Bootstrap
BouncyCastle
Castle.core
Dotless
HelpJuice.Client
IssueMaitnenance.CoreApp (and associated packages)
JQuery
LogMeIn.GoToCoreLib.Net
LogMeIn.GoToMeeting.Net
MailKit
MimeKit

All access to the tables happens in the Data_Access folder with the repositories

Some session variables that are used throughout the project are:
Session(“UID”) = Customer ID
Session(“GSSCustNo”) = Visual Customer Number for the Customer (What they use to log in)
Session(“UCID”) = Contact ID
Session(“EmpID”) = Employee ID
Session(“iUserType”) = 0=Employee, 1=Customer, 2=Contact
Session(“iDeptID”) = Employee Department ID (i.e. Service, R & D)
Session(“iTLGrp”) = Employee Specific Team ID (infrastructure Team, CSR, HR,A-Team,Axis, CI_Consulting, LMS)
Session(“ServGrp”) = Employee Group (ATG, CORE, Maintenance, PPT, Project Managers, Marketing )
Session(“DataSource”) = which data source is being used “gss2k19sw” or “gss2k19awsSQL”
Session(“DataCatalog”) = “IHOP_Net”, “IHOP_Test”

If you will be working with GAP EW you will need to make sure you have the following set up
C:\Websites\SVN folder will need to be created
You will need to move the SVN_File.exe to that folder (Please contact Erin or Andres for the exe)

Web.Config testing optional setups
To test the Service Web we have two databases and based on if you are using the test DB (GSS2K19SW.IHOP_Test) or the Live DB (GSS2K19AWSSQL.IHOP_Net)
Web.Config and Data_Access\gsDataAccess.vb needs to be updated based on the data base being use
Web.Config changes
How this should look for IHOP_Test
--These turn on the test database options
 <connectionStrings>
    <!--<add name="DefaultConnection" connectionString="data source=(localdb)\v11.0;initial catalog=aspnet-DevExp_Test-20170424101424;integrated security=SSPI" providerName="System.Data.SqlClient" />-->
	 <!--<add name="IHOP_Net" connectionString="Data Source=gss2k19sw;Initial Catalog=IHOP_Net;User ID=SWNetAll;Password=L$8f5G5MB$PhutE;" providerName="System.Data.SqlClient" />-->
	 <add name="IHOP_Test" connectionString="Data Source=gss2k19sw;Initial Catalog=IHOP_Test;User ID=SWNetTest;Password=u%6B5Ae%mVPNh3n;" providerName="System.Data.SqlClient" />
	  <!--<add name="IHOP_Net" connectionString="Data Source=10.10.10.12;Initial Catalog=IHOP_Net;User ID=SWNetAll;Password=L$8f5G5MB$PhutE;" providerName="System.Data.SqlClient" />-->
    <add name="SWStateInMemory" connectionString="Data Source=gss2k19sw;Initial Catalog=SWStateInMemory;User ID=SWStateManager;Password=qc=2ibel;" providerName="System.Data.SqlClient" />
	  <!--<add name="SWStateInMemory" connectionString="Data Source=10.10.10.12;Initial Catalog=SWStateInMemory;User ID=SWStateManager;Password=qc=2ibel;" providerName="System.Data.SqlClient" />-->
  </connectionStrings>
  <appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="PreserveLoginUrl" value="true" />
    <add key="ClientValidationEnabled" value="true" />
	  <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="vs:EnableBrowserLink" value="false" />
    <add key="MvcSiteMapProvider_UseExternalDIContainer" value="false" />
    <add key="MvcSiteMapProvider_ScanAssembliesForSiteMapNodes" value="true" />
    <add key="MvcSiteMapProvider_IncludeAssembliesForScan" value="SW_TestCust" />
    <!--add MS Graph variables here-->
    <add key="ida:AppID" value="60dceed9-cb49-4ef6-b1e5-8aac91869936" />
    <add key="ida:AppSecret" value="52-3S.qSOQTLyFNxBhGX0RCa:nm:Q.Q@" />
    <add key="ida:RedirectUri" value="https://www.gss-service.com/" />
    <add key="ida:AppScopes" value="User.Read Calendars.ReadWrite Mail.Read " />
    <!--add GoToMeeting variables here-->
    <add key="G2MConsumerKey" value="iIF760bhVXVsbYIjtCQ1EVb3eH9sqGG0" />
    <add key="G2MConsumerSecret" value="FemzxGqE0uDfJyAQ" />
    <add key="G2MUserName" value="sw@gssmail.com" />
    <add key="G2MPassword" value="1uYwQG4YoH" />
	  <!--Add PayPal variables here-->
	  <add key="PayPalClientId" value="ARdyWk9j3H5SXi0slkPQZzA8gr61yp2_scS2NA2u0DRMw_cN3Ib9ViEMkkvI55wz3sIzCi0oDt5qifUR" />
	  <add key="PayPalSecret" value="EBX6LwVz_BkxexqwhVoTuIC2SJxWpqZZbpJZKrVo4PsvljmjWbmerAC_OR9sYbJ3h8Z_BVONQQF-vAHT" />
	  <add key="PayPalClientId_Live" value="AYsC6MXDXwEASE2cmJTgWymwtFWFrcWOvOw9eO4dfMfrUWYYI-HB4xZUuoVARlyTs2N16LO4--H6Pbhg" />
      <add key="PayPalSecret_Live" value="EMF7injGBHgu_ETmeB9JbfFKK1ub9AupU34kJO5leq_YtjUctldTQeT2uM-toG2Tr23HqU1kXv4XglnL" />
	  <add key="PayPalMode" value="Prod" />
	  <!--add HelpJuice variables here-->
      <add key="HelpJuiceSecret" value="eec4e4a69d4d74ee03f5f45d3135da2c" />
      <add key="HelpJuiceKey" value="dd9fb1dd438bb4d95c57df58a153d86d" />
	  <!--(if testing purposes this would be "Sandbox" as the value)-->
	  <add key="DataSource" value="gss2k19sw" />
	  <add key="DataCatalog" value="IHOP_Test" />
	 
	  <!--<add key="DataSource" value="gss2k19awsSQL" />
	  <add key="DataCatalog" value="IHOP_Net" />-->
  </appSettings>
  <sessionState mode="Custom" customProvider="SqlInMemoryProvider">
      <providers>
        <add name="SqlInMemoryProvider" type="Microsoft.Web.SessionState.SqlInMemoryProvider" connectionString="data source=gss2k19sw;initial catalog=SWStateInMemory;User ID=SWStateManager;Password=qc=2ibel;" />
		  <!--<add name="SqlInMemoryProvider" type="Microsoft.Web.SessionState.SqlInMemoryProvider" connectionString="data source=10.10.10.12;initial catalog=SWStateInMemory;User ID=SWStateManager;Password=qc=2ibel;" />-->
      </providers>
    </sessionState>
 IHOP_Net section
  <connectionStrings>
    <!--<add name="DefaultConnection" connectionString="data source=(localdb)\v11.0;initial catalog=aspnet-DevExp_Test-20170424101424;integrated security=SSPI" providerName="System.Data.SqlClient" />-->
	 <!--<add name="IHOP_Net" connectionString="Data Source=gss2k19sw;Initial Catalog=IHOP_Net;User ID=SWNetAll;Password=L$8f5G5MB$PhutE;" providerName="System.Data.SqlClient" />-->
	 <!--<add name="IHOP_Test" connectionString="Data Source=gss2k19sw;Initial Catalog=IHOP_Test;User ID=SWNetTest;Password=u%6B5Ae%mVPNh3n;" providerName="System.Data.SqlClient" />-->
	  <add name="IHOP_Net" connectionString="Data Source=10.10.10.12;Initial Catalog=IHOP_Net;User ID=SWNetAll;Password=L$8f5G5MB$PhutE;" providerName="System.Data.SqlClient" />
    <!--<add name="SWStateInMemory" connectionString="Data Source=gss2k19sw;Initial Catalog=SWStateInMemory;User ID=SWStateManager;Password=qc=2ibel;" providerName="System.Data.SqlClient" />-->
	  <add name="SWStateInMemory" connectionString="Data Source=10.10.10.12;Initial Catalog=SWStateInMemory;User ID=SWStateManager;Password=qc=2ibel;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="PreserveLoginUrl" value="true" />
    <add key="ClientValidationEnabled" value="true" />
	  <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="vs:EnableBrowserLink" value="false" />
    <add key="MvcSiteMapProvider_UseExternalDIContainer" value="false" />
    <add key="MvcSiteMapProvider_ScanAssembliesForSiteMapNodes" value="true" />
    <add key="MvcSiteMapProvider_IncludeAssembliesForScan" value="SW_TestCust" />
    <!--add MS Graph variables here-->
    <add key="ida:AppID" value="60dceed9-cb49-4ef6-b1e5-8aac91869936" />
    <add key="ida:AppSecret" value="52-3S.qSOQTLyFNxBhGX0RCa:nm:Q.Q@" />
    <add key="ida:RedirectUri" value="https://www.gss-service.com/" />
    <add key="ida:AppScopes" value="User.Read Calendars.ReadWrite Mail.Read " />
    <!--add GoToMeeting variables here-->
    <add key="G2MConsumerKey" value="iIF760bhVXVsbYIjtCQ1EVb3eH9sqGG0" />
    <add key="G2MConsumerSecret" value="FemzxGqE0uDfJyAQ" />
    <add key="G2MUserName" value="sw@gssmail.com" />
    <add key="G2MPassword" value="1uYwQG4YoH" />
	  <!--Add PayPal variables here-->
	  <add key="PayPalClientId" value="ARdyWk9j3H5SXi0slkPQZzA8gr61yp2_scS2NA2u0DRMw_cN3Ib9ViEMkkvI55wz3sIzCi0oDt5qifUR" />
	  <add key="PayPalSecret" value="EBX6LwVz_BkxexqwhVoTuIC2SJxWpqZZbpJZKrVo4PsvljmjWbmerAC_OR9sYbJ3h8Z_BVONQQF-vAHT" />
	  <add key="PayPalClientId_Live" value="AYsC6MXDXwEASE2cmJTgWymwtFWFrcWOvOw9eO4dfMfrUWYYI-HB4xZUuoVARlyTs2N16LO4--H6Pbhg" />
      <add key="PayPalSecret_Live" value="EMF7injGBHgu_ETmeB9JbfFKK1ub9AupU34kJO5leq_YtjUctldTQeT2uM-toG2Tr23HqU1kXv4XglnL" />
	  <add key="PayPalMode" value="Prod" />
	  <!--add HelpJuice variables here-->
      <add key="HelpJuiceSecret" value="eec4e4a69d4d74ee03f5f45d3135da2c" />
      <add key="HelpJuiceKey" value="dd9fb1dd438bb4d95c57df58a153d86d" />
	  <!--(if testing purposes this would be "Sandbox" as the value)-->
	  <!--<add key="DataSource" value="gss2k19sw" />
	  <add key="DataCatalog" value="IHOP_Test" />-->
	 
	  <add key="DataSource" value="gss2k19awsSQL" />
	  <add key="DataCatalog" value="IHOP_Net" />
  </appSettings>
  <sessionState mode="Custom" customProvider="SqlInMemoryProvider">
      <providers>
        <!--<add name="SqlInMemoryProvider" type="Microsoft.Web.SessionState.SqlInMemoryProvider" connectionString="data source=gss2k19sw;initial catalog=SWStateInMemory;User ID=SWStateManager;Password=qc=2ibel;" />-->
		  <add name="SqlInMemoryProvider" type="Microsoft.Web.SessionState.SqlInMemoryProvider" connectionString="data source=10.10.10.12;initial catalog=SWStateInMemory;User ID=SWStateManager;Password=qc=2ibel;" />
      </providers>
    </sessionState>
gsDataAccess changes
Public Shared Function GetConnection(connectionType As ConnectionType) As SqlConnection
        Dim dbConnection As DbConnection

        Select Case connectionType
            Case ConnectionType.IHOP_Net
                dbConnection = New SqlConnection(System.Configuration.ConfigurationManager.ConnectionStrings("IHOP_Test").ConnectionString)
                'dbConnection = New SqlConnection(System.Configuration.ConfigurationManager.ConnectionStrings("IHOP_Net").ConnectionString)
            Case ConnectionType.SWStateInMemory
                dbConnection = New SqlConnection(System.Configuration.ConfigurationManager.ConnectionStrings("SWStateInMemory").ConnectionString)
                'Case ConnectionType.IssueMaint
                'dbConnection = New SqlConnection(System.Configuration.ConfigurationManager.ConnectionStrings("Issue_Maintenance").ConnectionString)
            Case Else
                dbConnection = New SqlConnection(System.Configuration.ConfigurationManager.ConnectionStrings("IHOP_Net").ConnectionString)
        End Select

        Return dbConnection
    End Function
---------------------------    
Regression Test Items
Customer - General
Customer - Contact Maintenance
    Customer Admin 
    Customer Contact 
    Employee Admin 
    Employee User
        8/31/2022 emarlow Cannot update email, should be disabled for GLO010, but are allowed to update email for Cusotmer Contacts

     
     Testing Cases
     9/01/2022 bbrambila
      Contact section for updating email and password for employees and Customer contacts.
      Cases on how needs to be tested with different users and different actions.
      For every change in the email and/or password test to  log in with the contact and new changes added.
                        
              --GSS Admin testing employees ------------------------------------------------------------------------------------------------
                        
                        Log in as: Admin GSS
                        Which users to test	: GSS Employees 
                        Actions: Change only Email	
                        Result: Updates email address in next tables
                                User_Logons
                                Cust_Contact_Master
                                Emp_Master          
                        Is Email textbox editable?: yes
                      ----------------------------------
                          
                        Log in as: Admin GSS
                        Which users to test: GSS Employees 
                        Actions: Change only Password	
                        Result: Updates password in  next table:
                                User_Logons

                                Send email to the contact

                      ------------------------------------   
                        Log in as: Admin GSS
                        Which users to test	: GSS Employees 
                        Actions: Change Email and Password	
                        Result: Updates email address in next tables: 
                              User_Logons
                              Cust_Contact_Master
                              Emp_Master

                              Updates password in  next table:
                              User_Logons

                              Send email to the contact
                      Is Email textbox editable?: yes
                      ----------------------------------------

              --GSS Admin testing  customer contacts -----------------------------------------------------------------------

                        Log in as: Admin GSS
                        Which users to test	: Customer Contacts 
                        Actions: Change only Email	
                        Result: Updates email address in next tables: 
                                User_Logons
                                Cust_Contact_Master        
                      Is Email textbox editable?: yes

                        -----------------------------------  
                        Log in as: Admin GSS
                        Which users to test	: Customer Contacts 
                        Actions: Change only Password	
                        Result: Updates password in  next table:
                                User_Logons

                                Send email to the contact
                      

                        ------------------------------------  
                        Log in as: Admin GSS
                        Which users to test	: Customer Contacts  
                        Actions: Change Email and Password	
                        Result: Updates email address in next tables:
                                User_Logons
                                Cust_Contact_Master
                            
                                Updates password in  next table:
                                User_Logons

                                Send email to the contact
                      Is Email textbox editable?: yes

                      ---------------------------------------

              --Employee testing  Employee ------------------------------------------------------------------------------------------
                        Only can update his own password, email textbox is disabled

                        Log in as: Employee
                        Which users to test	:Employee 
                        Actions: Change only Email	
                        Result: Email textbox is disabled      
                      Is Email textbox editable?: No

                        -----------------------------------------------  
                        Log in as: Employee
                        Which users to test	: Employee 
                        Actions: Change only Password	
                        Result: Updates password in  next table:
                                User_Logons

                                Send email to the contact

                        --------------------------------------  
                        Log in as: Employee
                        Which users to test	: Employee 
                        Actions: Change Email and Password	
                        Result: Email textbox is disabled  so, just will update password     
                        Is Email textbox editable?: No

                      -------------------------------------------

               --Employee testing  Customer Contacts ---------------------------------------------------------------------------------------
                        
                        Log in as: Employee
                        Which users to test: Customer Contacts
                        Actions: Change only Email	
                        Result: Updates email address in next tables: 
                                User_Logons
                                Cust_Contact_Master  

                      Is Email textbox editable?: yes

                        -----------------------------------------------  
                        Log in as: Employee
                        Which users to test	: Customer Contacts
                        Actions: Change only Password	
                        Result:  Updates password in  next table:
                                  User_Logons

                                  Send email to the contact

                      --------------------------------------  
                        Log in as: Employee
                        Which users to test	: Customer Contacts
                        Actions: Change Email and Password	
                        Result: Updates email address in next tables: 
                                User_Logons
                                Cust_Contact_Master
                              
                                Updates password in  next table:
                                User_Logons

                              Send email to the contact    
                        Is Email textbox editable?:Yes

                      


              -- Customer  Admin testing  Customer Contacts ---------------------------------------------------------------------------------------
                       
                        Log in as: Customer  Admin 
                        Which users to test: Customer Contacts
                        Actions: Change only Email	
                        Result: Updates email address in next tables: 
                                User_Logons
                                Cust_Contact_Master  

                      Is Email textbox editable?: yes

                        -----------------------------------------------  
                        Log in as: Customer  Admin 
                        Which users to test	: Customer Contacts
                        Actions: Change only Password	
                        Result:  Updates password in  next table:
                                  User_Logons

                                  Send email to the contact

                      --------------------------------------  
                        Log in as: Customer  Admin 
                        Which users to test	: Customer Contacts
                        Actions: Change Email and Password	
                        Result: Updates email address in next tables: 
                                User_Logons
                                Cust_Contact_Master
                              
                                Updates password in  next table:
                                User_Logons

                              Send email to the contact    
                        Is Email textbox editable?:Yes

                      -------------------------------------------


            --Customer Contacts testing  Customer Contacts ---------------------------------------------------------------------------------------
                        Customer Contacts only can update his own data


                        Log in as: Customer  Customer Contact 
                        Which users to test: Customer Contact
                        Actions: Change only Email	
                        Result: Updates email address in next tables: 
                                User_Logons
                                Cust_Contact_Master  

                      Is Email textbox editable?: yes

                        -----------------------------------------------  
                        Log in as: Customer  Customer Contact 
                        Which users to test	: Customer Contact
                        Actions: Change only Password	
                        Result:   Updates password in  next table:
                                  User_Logons

                                  Send email to the contact

                      --------------------------------------  
                        Log in as: Customer  Customer Contact 
                        Which users to test	: Customer Contact
                        Actions: Change Email and Password	
                        Result: Updates email address in next tables: 
                                User_Logons
                                Cust_Contact_Master
                              
                                Updates password in  next table:
                                User_Logons

                                Send email to the contact  

                                 Is Email textbox editable?:Yes

                      
               --Creating new contacts--------------------------
                              Log in as: admin
                                Which users to test	:any user
                                Actions: Create New contact	
                                Result: Updates email address in next tables: 
                                User_Logons
                                Cust_Contact_Master

                                if it is employee then update
                                Emp_Master

                                Updates password in  next table:
                                User_Logons (if password was not typed, then it assigns a random password)

                                Send email to the contact 

               --Update any contact data but email/password--------------------------
                              Check that email and password are not updated when another data of the contact needs to be udpated, example: update only  title
                              or status and see email and passwor still remain the same

                                Log in as: any user
                                Which users to test	:any user
                                Actions: Modify any data that is not email or password
                                Result: 
                                
                                Cust_Contact_Master

                          
 -------------------------------------------------------------------------------------------------------------------------------------------------------                             
                       


Call Information
  Create Call Customer
  Create Call Employee
  Create Cloud Request Customer
  Create Cloud Request Employee
  Edit Call Customer
  Edit Call Employee
    Test Page load 
    Test Save 
    Test Open call from queue

-------------------------------
	Edit Quote - Allow users to change the Call Reference
   9/06/2022 bbrambila
      New functions and SP created
      View: Quotes/F_QuoteRequestInternal  (code were added in the Reference No section)
      Quote Controller: SaveCallReferenceFromQuote
      Quote Repository: SaveCallReferenceFromQuote
       SP: Update_CallReferenceOnQuote

 










