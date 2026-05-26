#salesforce-training

 Phase-1: 1:  CRM-Customer Relationship Management
    Designed to manage company's relationships between the current and potential customers
 2:  Why companies use salesforce?
     To manage sales,service,marketing and many more on one platform rather than using disconnected systems.
     to reduce time efficiency etc
 3:  Account: Represents the company or consumer that business is doingwith.
     Contact: A person associated with account.
     Oppurtunity: A sales transaction that is in progress.
REAL WORLD MAPPING:
    Banking System:
      Acount: Bank Customer Account
      Lead: Person interested in opening account/loan
      Contact: Account holder in the bank
      Oppurtunity: Loan or credit application
 
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------- 
   Phase-2: Salesforce Platform:
         It is a cloud based platform used to build CRM application and business applications without needing  heavy infrastructure setup
         It helps companies:
         ->store customer and business data
         ->automate business processes
         ->create apps
         ->generate reports and dashboards
         ->manage users and security
       Ex: A college can use salesforce to manage student admissions,faculty details,courses,fees and placements.
    a)App: An app is a collection of related tabs,objects and features grouped together for a specific purpose.
         It acts like a complete working area for users.
         Example: A college management app may contain student tab,facukty tab,course tab,fee tab etc.
         ->Users open one app and access everything related to that work.
    b)Object: An object is like a database table used to store data.
         -->Each object contains records(rows) and fields(columns).
        Example: Student Name      Roll No       Branch
                   Ravi              101           CSE
                   Riya              102           ECE
                Here: object=student
                      fields=student name,roll no,branch
                      records=ravi's data,riya's data
         Types: 1.Standard objects(already provided by Salesforce).
                2.Custom object(created by users).
    c)Tab: A tab is used to open and access an object or feature in Salesforce.
           It provides the user interface for viewing records.
         Example: If student object is created then salesforce can create student tab
                  when user clicks the student tab; they can view students,add new studenrs and can edit student records.

Configuration and Coding: 
                   Configuration uses built-in "point and click" tools,while coding involves writing custom program logic using languages like Apex.
   Configuration examples:
           1.Creating custom object: Creating student object to store student details.
           2.Creating validation rules: Making the phone number field mandatory before saving a record.
   Coding examples:
           1.Apex trigger: Automatically sending an email when new contact is created.
           2.Lightnig Web component(LWC): Building a custom student dashboard with buttons and chart.

  System design of college management:
      App Name: Campus Connect
      Objects:
      ->Student Object(Std name,roll no. , branch,year,phone number)
      ->Faculty Object(Faculty name,Department,Subject,Email)
      ->Course Object(Course name,Course codes,credits)
      ->Attendance Object(Std name,subject,Attendance percentagetage)
      ->Fee Object(Std name,Total fee,paid amount,due amount)

  User Interaction Flow:
        College management App
                 |
        Objects:
        Student->Faculty->Course->Attendance->Fee
                 |
         Users interact through tabs
                 |
         Data stored in salesforce database    

-------------------------------------------------------------------------------------------------------------------------------------------------------------------
Phase 3:a) *Difference between App,object,record and field:*
        **App**                    |          **object**       |          **Record**        |              **Field**
It is a collection of related      |   A database that stores  |   A single row/data entry  |   A column/attribute that stores the 
tabs,objects and tools used for    |        the data.          |     inside an object.      |       specific information in a reocrd. 
specific purpose.                  |                           |                            |
 
 Real life Example:
    App:College Management App
    Object: Student Object
    Record:Ravi's data(from the above example of object)
    Field:Std name,roll no,branch
b)Standard objects vs Custom objects:
                **Standard Objects**                                  |                              **Custom Objects**
    1.These are pre-built and provided by the salesforce.             |                 1.Here objects are created by users according to their
                                                                      |                          business requirements.
    2.The customization of these objects are limited.                 |                 2.These objects are fully customizable.
    3.The naming of these objects are normal.                         |                 3.These names end with _c.
    4.Examples:Account,contact,opportunity,Lead                       |                 4.Student,Library,Hostel,Attendance etc
                                                                      |
c) College data Model:
   a)Objects: Student obj(Stores std details)
              Faculty obj(Stores faculty ingormation)
              course obj(Stores course details)
              Department obj(Stores department datails)
              Enrollment obj(Connects stds and courses)
     -->These objects are custom objects which were created by the users.
  b) Relationships:
      **Parent object**              |            **Child object**                  |              **Relationship type**
      Department->Faculty            |           Lookup/Master detail               |           One department has many faculty
      Department->Course             |            Lookup/master detail              |           One department has many courses
      Student->Enrollment            |               Master detail                  |         One student can enroll many courses                                         Course->Enrollment            |               Master detail                  |       One course can have many std enrollments
   c)*college Data Model Diagram*:
   
                                             Department                                         **Explanation**:
                                                 |                                                ->Department manages faculty and courses.
                                  --------------------------------------                          ->Students enroll in courses through enrollment object.
                                  |                                    |                          ->Enrollment acts as  a junction object between student and 
                               Faculty                               Course                          course.
                                                                       |
                                                                    Enrollment
                                                                       |
                                                                     Student 
                                                                     
d)Formula Fields:
    A formula field automatically calculates values using formulas.
    Example:1) Student Full name: Fields could be first_name and last_name          2)Percentage calculation field:Marks_obtained and total_marks
         If name is ravi kumar then first_name is ravi and last_name is kumar.         Formula:(marks_obtained/total_marks)*100
    formula: first_name & " "& Last_name.(Combines two fields automtically) 

e)Validation rules:
     Validation rules prevent users from entering incorrect data.
     Example:1)Marks cannot exceed total marks
             2)Email cannot be empty.

f)Why structured enterprise data matters?
   Structured enterprise data is very important in salesforce because it helps organizations store,manage and analyze information properly. 

-------------------------------------------------------------------------------------------------------------------------------------------------------------------
Phase 4: 
a)Flow Builder: It is a point and click automation tool in salesforce used to automate business processes without writing code.
  It help users:
  ->collect data                                                              ->create approval processes 
  ->guide users through screens                                               ->send emails/notifications
  ->Update record automatically

b)Types of flows:
  a)Screen flow: Screen flow is a flow that interacts with users through screens.
    It mainly used when:
    ->users need to enter data.     ->users need guidance steo by step.   ->forms or wizards are required.
    Ex:College admission form
    Uses: surveys,registration forms,complaint forms etc
  b)Record-triggered flow:A record triggered flow runs automatically when a record is: created,updated,deleted.
    ->no user interaction is required.
    Ex: when a new student record is created:
       ->send welcome email automatically   ->assign mentor automatically  ->update admission status
    Uses: auto-update fields,send notifications,create related reocrds,approval automation,status updates.
  c)Automation ideas:
      1)Student admission automation
         when a student application is submitted: create student record,send confirmation email,assign department automatically
         Flow type: Record triggered flow
      2)Library book issue system:
         A librarian enters student ID and book details through screens(screen flow)
         The flow: checks availability,updates issue status,sets return date
      3)Attendance alert system
        If attendance goes below 75: send warning email to student, notify class mentor
        Flow type: record-triggered flow
      4)Hostel room allocation(screen flow)
       Student selects hostel preferences using screens
       ->checks available rooms,allocate room automatically,sends hostel confirmation
      5)Fee payment status automation(record triggered flow)
        when a students pays college fee: update records,send email notification, create receipt record
         
   d)                                                  Flow diagram:
             <img width="500" height="500" alt="flow diagram" src="https://github.com/user-attachments/assets/efbf5f52-019c-4679-870e-f6d0e113b804" />
   e) Manual process: It relies on human effort and judgement to execute tasks,offering high flexibility but slower speeds.
     Automated process: An automated process uses technology and software scripts to execute workflows without human intervention
            <img width="400" height="400" alt="man and auto" src="https://github.com/user-attachments/assets/42c920e5-64b2-4bf3-8652-37c23c2eb618" />
   f)Why automation matters in enterprise systems?
     Automation is very important in enterprise systems because it improves efficiency, accuracy, and speed. In organizations like colleges and companies, many          repetitive tasks are performed every day. Automation reduces manual work and saves time for employees.
       Using Salesforce Flows:
        ->Data can be processed automatically
        ->Errors are reduced
        ->Notifications and emails are sent instantly
        ->Records are updated in real time
        ->Employees can focus on important tasks instead of repetitive work
        For example, in a college admission system, automation helps students receive faster responses and improves the overall admission process. Enterprise              automation also increases productivity and provides a better user experience.
   
   ---------------------------------------------------------------------------------------------------------------------------------------------------------------    Phase 5: 
   Apex: Apex is a programming language developed by Salesforce that is used to add custom business logic in Salesforce applications.
         It is similar to Java and is mainly used when Salesforce configuration tools (like Flow or Validation Rules) are not enough.
         Using Apex, developers can:
         ->Automate complex processes
         ->Create custom calculations
         ->Integrate external systems
         ->Write triggers and classes
         ->Perform advanced validations
         Example: When a student’s fee payment is completed, Apex can automatically generate a receipt and send an email notification.

   Flow vs Apex:
           Feature             | Flow              | Apex                             
          -------------------  | ----------------- | -------------------------------- 
           Type                | Declarative Tool  | Programming Language             
           Coding Required     | No                | Yes                              
           Easy for Admins     | Yes               | No                               
           Complexity Handling | Medium            | High                             
           Best For            | Simple automation | Complex business logic           
           Maintenance         | Easier            | Requires developer               
           Example             | Auto email alerts | Integration with payment gateway 
   Configuration vs Coding:
             Configuration                  | Coding                  
            ------------------------------  | ----------------------- 
             Uses clicks not code           | Uses programming        
             Faster development             | More flexible           
             Easy maintenance               | Requires developers     
             Used for simple tasks          | Used for advanced logic 
             Example: Flow, Validation Rule | Example: Apex Trigger   
     Real Examples Where Apex Is Needed
     Example 1: Automatic Fee Receipt Generation
                When a student pays fees:
               ->Apex creates a PDF receipt
               ->Sends receipt email automatically
    Example 2: External Payment Gateway Integration
           College system connects with:
           Razorpay
            Paytm
            Apex is used to:
           ->Send payment request
           ->Receive payment status
           ->Update student records
    Example 3: Attendance Warning System
               If attendance falls below 75%:
               ->Apex checks attendance weekly
               ->Sends warning email to students and parents
               ->Updates student status automatically
              
   Integrated College Management System Design:
             Overview
             The College Management System in Salesforce helps manage:
              ->Admissions
              ->Student records
              ->Fees
              ->Attendance
              ->Courses
              ->Faculty information
          -->CRM in College Management
             CRM helps maintain relationships with:
              ->Students
              ->Parents
              ->Faculty
              ->Alumni
      Example:
           A student inquiry becomes an admission opportunity.
 Objects used:
          | Object     | Purpose                   |
          | ---------- | ------------------------- |
          | Student    | Stores student details    |
          | Course     | Stores course information |
          | Faculty    | Faculty records           |
          | Attendance | Tracks attendance         |
          | Fees       | Stores payment details    |
          | Admission  | Admission process details |
Relationships:
          | Relationship         | Type        |
          | -------------------- | ----------- |
          | Student → Course     | Many-to-One |
          | Course → Faculty     | Many-to-One |
          | Student → Attendance | One-to-Many |
          | Student → Fees       | One-to-Many |
Validation Rules
               Examples:
                ->Phone number must contain 10 digits
                ->Attendance cannot exceed 100%
                ->Fee amount cannot be negative
                ->Email must contain “@”
        Example:Attendance__c > 100
Flow Automation
        Record Triggered Flow 
            When admission status becomes “Approved”:
            ->Student record is created automatically
            ->Welcome email is sent
            ->Fee record is generated
            ->Screen Flow
        Students can:
            ->Submit admission forms
            ->View fee details
            ->Update profile information
            ->Apex Usage in the System
  Apex Trigger:
          When fee payment is completed:
           ->Receipt generated automatically
           ->Student payment status updated
  Apex Integration:
         Connects Salesforce with:
         ->Payment gateways
         ->SMS services
         ->University portals      

System work flow:

                                                  Student Applies
                                                         ↓
                                                Admission Record Created
                                                         ↓
                                               Validation Rules Check Data
                                                         ↓
                                            Flow Automates Admission Process
                                                         ↓
                                              Apex Handles Complex Logic
                                                         ↓
                                                Student Record Generated
                                                         ↓
                                               Fees and Attendance Managed
                                                         ↓
                                             Reports and Notifications Sent
Pseudocode examples:
  Ex-1: Student Admission Approval:
                        START 
                         IF student_marks >= 75 THEN
                           Display "Admission Approved"
                         ELSE
                            Display "Admission Pending Review"
                        END IF
                        STOP
Ex-2: Automatic fee reminder:
                START
           FOR each student
              IF fee_status = "Pending" THEN
                  Send reminder email
              END IF
           END FOR
           STOP
Ex-3: Attendance warning system:
                START
                IF attendance_percentage < 75 THEN
                   Create warning message
                   Notify student
                END IF
Why Enterprise Systems Eventually Need Programming?
   Enterprise systems like college management systems, banking systems, hospital systems, and CRM platforms initially use configuration tools because they are        fast and easy to build. Features like objects, fields, validation rules, and flows help automate many business processes without coding.

   However, as organizations grow, their requirements become more complex. Simple configuration is often not enough to handle advanced business logic, integrations, calculations, and large-scale automation. At this stage, programming becomes necessary.             
  Programming languages like Apex in Salesforce help developers:
  ->Build complex automation
  ->Integrate external systems
  ->Handle bulk data processing
  ->Create custom business logic
  ->Improve system flexibility and scalability
For example, a college management system may later require:
  ->Automatic scholarship calculation
  ->Integration with payment gateways
  ->Real-time notifications
  ->Complex attendance analytics
  ->Custom approval processes
These advanced requirements cannot always be achieved using only configuration tools. Therefore, enterprise systems eventually need programming to become more powerful, intelligent, and scalable.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------
Phase 6: 
  1.**SOQL**:
  SOQL stands for Salesforce Object Query Language.
    It is used to retrieve records from Salesforce objects, similar to how SQL is used in databases.
    SOQL helps developers fetch data from objects like Account, Contact, Opportunity, Case, etc.
    Example: SELECT Name, Email FROM Contact
    -->This query retrieves the Name and Email fields from the Contact object.
       **Uses of SOQL**:
         ->Retrieve records from Salesforce
         ->Filter data using conditions
         ->Sort records
         ->Access related object data
         ->Use in Apex classes and triggers
2.**What is an Apex Trigger?**
   An Apex Trigger is a piece of Apex code that automatically executes before or after events occur on Salesforce records.
    Triggers help automate custom business logic when records are:
     ->Inserted
     ->Updated
     ->Deleted
     ->Restored         
    It is used to retrieve records from Salesforce objects, similar to how SQL is used in databases.
      SOQL helps developers fetch data from objects like Account, Contact, Opportunity, Case, etc.
    Example:
     trigger ContactTrigger on Contact (before insert) {
    for(Contact con : Trigger.new) {
        con.Description = 'New Contact Created';
    }
}
    This trigger automatically sets a description before a Contact record is inserted.
   -->Common Uses:
   ->Validation
   ->Automatic field updates
   ->Sending notifications
   ->Preventing incorrect data
   ->Integrating with external systems
 **Flow vs Trigger:**                                                                                    Example:
    | Feature       | Flow                        | Trigger                        |                   Flow: Send email when case is created
    | ------------- | --------------------------- | ------------------------------ |                   Trigger:Complex validation across multiple objects
    | Type          | Declarative Tool (No Code)  | Programmatic Tool (Code)       |
    | Language      | Drag-and-drop               | Apex                           |
    | Complexity    | Simple to medium automation | Complex automation             |
    | User Friendly | Easy for admins             | Requires programming knowledge |
    | Performance   | Slower for heavy logic      | Faster for complex processing  |
    | Maintenance   | Easier                      | Requires developers            |
    | Best For      | Simple approvals, updates   | Advanced business logic        |
    
**Before trigger vs after trigger:**                                                                   -->Before trigger example:
     | Feature                  | Before Trigger             | After Trigger           |                    before insert, before update
     | ------------------------ | -------------------------- | ----------------------- |                     ->used for validation
     | Runs                     | Before record is saved     | After record is saved   |                     ->updating field values before save
     | Main Purpose             | Validate or modify data    | Work with saved records |                -->After trigger example:
     | Can Change Field Values? | Yes                        | No                      |                     after insert, after update
     | Record ID Available?     | Usually No (before insert) | Yes                     |                      used for:
     | Faster?                  | Yes                        | Slightly slower         |                      ->sending emails, creating related records etc.
Simple Real-Time Example:
 **Before Trigger**
    A company automatically sets:
    Status = "New"
    before saving a Case.
**After Trigger**
    After saving an Opportunity:
    Send notification email
    Create invoice record
     Update related reports  

4. Trigger Use Cases (5 Examples)
    1. Automatic Welcome Email
       When a new customer Contact is created in Salesforce, an Apex Trigger automatically sends a welcome email.
    2. Update Account Status
       When all Opportunities of an Account are closed successfully, the trigger automatically updates the Account status to “Active”.
    3. Prevent Invalid Data
       A trigger prevents users from saving employee records if the salary value is negative.
    4. Create Follow-Up Task
       When a high-priority Case is created, the trigger automatically creates a follow-up task for the support team.
    5. Attendance Warning System
       In a college management system, if a student’s attendance falls below 75%, the trigger automatically creates a warning notification.     
5.Query Examples (Your English Query Ideas)
   Example 1
    ->Get all students whose attendance is below 75%
   Example 2
    ->Show all contacts created this month
   Example 3
    ->Find all opportunities with amount greater than 1 lakh
   Example 4
    ->Display all employees working in the HR department
   Example 5
    ->Retrieve all cases with status = Open
   Example 6
    ->Get customers from Hyderabad city
   Example 7
    ->Show all products that are out of stock
6. Reflection
Why Enterprise Systems React Automatically to Data Changes?
    Enterprise systems are designed to handle large amounts of data and business processes efficiently. Manual monitoring of every change is difficult, time-consuming, and error-prone. Therefore, enterprise systems automatically react to data changes using automation tools like Flows and Apex Triggers.
Whenever a record is created, updated, or deleted, the system can immediately perform related actions such as:
->Sending notifications
->Updating related records
->Validating data
->Creating tasks
->Triggering approvals
->Generating reports
For example:
In banking systems, transactions automatically update account balances.
In hospital systems, patient status updates can notify doctors.
In Salesforce CRM, creating a Case can automatically assign it to a support agent.
Automatic reactions improve:
->Speed
->Accuracy
->Productivity
->Data consistency
->Customer experience
Thus, enterprise systems use automation to ensure real-time processing and smooth business operations without depending completely on manual work.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------
Phase 7:
   **1.Why testing matters?**
     Testing is very important in enterprise software systems like Salesforce because businesses depend on the software for daily operations.
      **Importance of Testing**
         -->Ensures Quality
           Testing checks whether the application works correctly.
         -->Prevents Errors
           Bugs in enterprise systems can affect customers, employees, and company data.
         -->Protects Data Integrity
           Salesforce stores sensitive business information such as customer details and sales records.
         -->Improves Reliability
           Proper testing ensures workflows, automation, triggers, and integrations work smoothly.
         -->Required for Deployment
            Salesforce requires minimum test coverage before deploying Apex code to production.
         Example:
         If a trigger automatically creates a Case when a customer complaint is submitted:
         Testing verifies the Case is created correctly.
         It checks whether wrong or duplicate records are avoided.
  **2. What is Asynchronous Apex?**     
    Asynchronous Apex means running processes in the background instead of immediately.
    It is used when operations:
       ->Take a long time
       ->Need large data processing
       ->Should not slow down users
       Types of Asynchronous Apex
        1. Future Methods
            Used for simple background tasks.
             Example:Sending confirmation emails
             Updating records after a transaction
             @future
               public static void sendEmail() {
               // background process
             } 
        2. Queueable Apex
              More advanced than Future Methods.
              Features:
              Supports complex processing
              Allows job chaining 
              Example:
               System.enqueueJob(new MyQueueableClass());
        3. Batch Apex
             Processes large numbers of records in batches.
            Used for:
            Data cleanup
            Mass updates
            Example:
           Updating 1 million customer records.
        4. Scheduled Apex
            Runs at a specified time automatically.
            Example:
            Daily report generation at 9 PM.
**3. What is Salesforce DX?**
       Salesforce DX (Developer Experience) is a modern development toolset provided by Salesforce.
       It helps developers:
       ->Build applications faster
       ->Use source-driven development
       ->Work in teams efficiently
         Main Features:
         -->Scratch Orgs
            Temporary Salesforce environments for development and testing.
         -->CLI (Command Line Interface)
            Developers can manage Salesforce using commands.
         Example:   sfdx force:org:create
         Version Control Integration
         Works with tools like:
          Git
          GitHub
         Continuous Integration/Deployment
         Supports automated testing and deployment.
**4. Complete System Workflow (End-to-End Explanation)**
   Example Scenario:
     Customer submits a support request.
 Step 1: User Enters Data
          Customer fills a complaint form.
       Example fields:
        Name
       Product
      Issue Description
 Step 2: Data Stored in Salesforce
         Information is saved in objects such as:
         Account
         Contact
         Case
 Step 3: Validation Rules Execute
         Salesforce checks:
         Required fields
         Correct formats
         Duplicate prevention
      Example:
       Email cannot be blank. 
Step 4: Trigger Executes
        An Apex Trigger runs automatically.
     Example:
    Assigns priority based on complaint type.
    trigger CaseTrigger on Case(before insert) {
     for(Case c : Trigger.new) {
        c.Priority = 'High';
        }
    }
Step 5: Flow/Automation Runs
       Flows may:
        Send email alerts
        Notify managers
        Create tasks
Step 6: Asynchronous Processing
          Background jobs may:
             Send notifications
             Generate reports
             Update external systems
Step 7: Testing Phase
          Developers execute:
          Unit tests
          Integration tests
          User acceptance tests  
Step 8: Deployment Using Salesforce DX
         Code moves from:
          Sandbox → Production
            Using:
              Git
              CI/CD pipelines
              Salesforce DX tools
Step 9: Monitoring and Maintenance
           Admins monitor:
             Errors
             Logs
             Performance
             Security 
 **5. Important Test Cases (Examples)**
      Test Case 1: Required Field Validation
           Objective:
              Check whether mandatory fields are enforced.
                Steps:
                 Create Case without Email
                 Save record
          Expected Result:
            Error message displayed.            
       Test Case 2: Trigger Functionality
                  Objective:
                      Verify trigger assigns High Priority.
                  Steps:
                   Create complaint Case
                   Save record
                Expected Result:
                  Priority becomes “High”.
        Test Case 3: Duplicate Prevention
                 Objective:
                    Ensure duplicate contacts are blocked.
                 Expected Result:
                    Duplicate warning shown.    
        Test Case 4: Flow Automation
                    Objective:
                       Verify email notification is sent.
                    Expected Result:
                       Manager receives email alert.
        Test Case 5: Batch Apex Processing
                    Objective:
                       Check large record updates.
                    Expected Result:
                       All records updated successfully without failure.
        Test Case 6: User Permissions
                       Objective:
                         Verify security access.
                       Expected Result:
                         Unauthorized users cannot edit restricted records.               
**6.Why Enterprise Software Development Needs Structured Workflows?**
        Enterprise systems are large and complex. Structured workflows are necessary because they:
         -->Improve Organization
              Teams can clearly understand:
                 Development
                 Testing
                 Deployment
                 Maintenance                     
          -->Reduce Errors
              Defined processes reduce:
                Bugs
                Data loss
                Deployment failures
          -->Support Team Collaboration
                  Developers, testers, and admins can work together efficiently.
          -->Ensure Security and Compliance
                  Businesses must protect customer and company data.
          -->Enable Scalability
                  Structured workflows help systems grow as organizations expand.
          -->Increase Reliability
                  Automation, testing, and monitoring make enterprise systems more stable and trustworthy.   

-------------------------------------------------------------------------------------------------------------------------------------------------------------- Phase 8:                
     1.**What is LWC?**   
            Lightning Web Components (LWC) is a modern framework in Salesforce used to build fast and interactive user interfaces (UI) for Salesforce applications.
              It is based on: 
              HTML,JavaScript,CSS,Web Standards
              LWC helps developers create reusable components like:
              Forms,Buttons,Tables,Dashboards,Record pages
               Example: A “Student Registration Form” in Salesforce can be created using LWC with:
               Input fields,Save button,Validation messages,Dynamic updates
     2.**Why Salesforce Uses LWC?**
        Salesforce uses LWC because it is:
        ->Faster
           LWC uses modern browser technologies, so pages load quickly.
        ->Reusable
           One component can be reused in multiple pages.
        ->Easy to Maintain
           Code is separated into small components.
        ->Better Performance
           Works efficiently with Salesforce data.
        ->Modern Development
           Uses standard JavaScript instead of older proprietary frameworks.
      3.**UI screen(examples)** 
           Suppose you create a Property Management System in Salesforce.
            Possible UI screens:
            -->Home Screen                                             -->Property List Screen
                Navigation menu                                             Table showing all properties
                Property statistics                                         Search bar
                Quick actions                                               Filter options
            -->Property Form Screen                                     -->Property Details Screen
                Property Name                                              Full property information
                Location                                                    Edit/delete buttons
       4.**Components breakdown**:
           In LWC, every UI part is a component.
              Example for Property Management App:
               | Component    | Purpose                |
               | ------------ | ---------------------- |
               | propertyForm | Add/Edit property      |
               | propertyList | Display all properties |
               | propertyCard | Show one property      |
               | searchBar    | Search properties      |
               | navbar       | Navigation menu        |
       5.**Frontend vs Backend Logic**
           _Frontend Logic (Client Side)_
           This is what users see and interact with.
           Technologies:
           HTML,CSS,JavaScript
           Responsibilities:
           Buttons,Forms,Validation,UI Design,User interactions
           Example: When user clicks “Save”, JavaScript checks:Is Property Name empty?; Is Price valid?
           _Backend Logic (Server Side)_
             This handles data processing in Salesforce.
             Technologies:
             Apex,SOQL,Salesforce Database
             Responsibilities:
             Save records,Fetch records,Business logic,Security
              Example: Apex code saves property data into Salesforce objects.
        6. **Reflection**
              Lightning Web Components make Salesforce applications:
               Faster,Cleaner,Interactive,Easy to use
                   LWC follows modern web development standards, which helps developers build professional enterprise applications efficiently.
               By separating:
                    UI components,Business logic,Database operations
                     Salesforce applications become:
              Scalable,Reusable,Maintainable
                 LWC is important because modern enterprise systems require:
                      Dynamic interfaces,Real-time updates,Better user experience,High performance
              That is why LWC is now the preferred UI framework in Salesforce. 
              
 -----------------------------------------------------------------------------------------------------------------------------------------------------------------             
              
              
           
