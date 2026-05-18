salesforce-training

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
Phase 3: *Difference between App,object,record and field:*
        **App**                    |          **object**       |          **Record**        |              **Field**
It is a collection of related      |   A database that stores  |   A single row/data entry  |   A column/attribute that stores the 
tabs,objects and tools used for    |        the data.          |     inside an object.      |       specific information in a reocrd. 
specific purpose.                  |                           |                            |
 Real life Example:
    App:College Management App
    Object: Student Object
    Record:Ravi's data(from the above example of object)
    Field:Std name,roll no,branch
Standard objects vs Custom objects:
                **Standard Objects**                                  |                              **Custom Objects**
    1.These are pre-built and provided by the salesforce.             |                 1.Here objects are created by users according to their
                                                                      |                          business requirements.
    2.The customization of these objects are limited.                 |                 2.These objects are fully customizable.
    3.The naming of these objects are normal.                         |                 3.These names end with _c.
    4.Examples:Account,contact,opportunity,Lead                       |                 4.Student,Library,Hostel,Attendance etc
                                                                      |

                                                                      
