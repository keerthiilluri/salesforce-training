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
