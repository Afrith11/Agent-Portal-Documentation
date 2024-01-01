![](https://portal.mawarid.com.sa/System/assets/images/mawarid-logo-2.png)

## **Introduction**

  Al Mawarid is a manpower recruiting company which is located in Saudi Arabia. This Recruiting company has recruit employees from different countries for different vacancies through the different agents or agencies. This agent portal has the record of the agent details, recruitment project and their records of recruiting employee details and the progress stage of employee's Application, Interview and Flight plan. Before that, here we can see how the new agent is coming into this agent portal with username and password.

![](./Assets/IR%20Login%20page.png)

>  - By Login through this Portal Mawarid System, it displays the IR System dashboard. 
>  - To `Enable` the `Dev mode` by clicking the profile icon on the top right of the dashboard.
>  - After that, click `recruitment -> agent` on the left top menu icon near home icon.

![](./Assets/Agent%20sidebar%20IR.png)  

>  - In the Agent menu, click create icon `+` to add details.

![](./Assets/Create%20Agent.png) 

>  - Add identification details of Agent name, Contact person, Country, City and License Number and Agent Id will created automatically by default. 
>  - Add Contact details of Agent's Email, Mobile number, Street, Postal code, Telephone number, Fax Number, PostBox Number, Website and Address.
>  - Add Bank deatils of Agent's Bank Name, Bank Account Name, Branch Name, IBAN, SWIFT code and Notes in the create form to join as an agent.
>  - After joined as an agent, they will receive a Login Credentials to access agent portal and their details will show in the My Profile page in agent portal. 

## **Agent Portal Login Page**

![](./Assets/Agent%20Portal%20Login%20page.png)

## **API** 

  - Method - POST
  - URL - https://portal.mawarid.com.sa/SystemApi//api/v1/org/login?user-id=a.hyder

## **Agent Portal Welcome page** 

It contains 5 menubar in the left side of the user and they are,

![](./Assets/Agent%20Portal%20Sidebar.png)

1. My Profile

2. Recruitment Project

3. Application             

4. Interview

5. Flight Plan

## **My Profile**

>  - My Profile, Which means an Agent's Profile. It actually contains a full details of the agent such as `Agent Name, Agent id, Address, Contact details, Bank details and Website.`
>  - The data of an agent was reflect from the Portal Mawarid System while creating a new agent access and assigning role.

## **API** 

  - Method - GET
  - URL - https://portal.mawarid.com.sa/SystemApi/api/v1//entitytype/dynamic/queryexecute?queryRecId=90&formRecId=&AgentId=AGN0000010&UserId=AGN0000010

## **Recruitment Project**

  - A Recruitment Project in a recruitment company involves the systematic process of identifying, sourcing, assessing and hiring candidates for specific job positions on behalf of client organizations.
  - It typically includes defining the job descriptions, advertising the positions, screening resumes, conducting inteviews and facilitating the hiring process.
  - The goal is to match qualified candidates with the client's needs, ensuring a successful and efficient recruitment outcome.

## **API** 
  
  - Method - GET
  - URL -https://portal.mawarid.com.sa/SystemApi/api/v1//entitytype/dynamic/queryexecute?queryRecId=182&formRecId=10967&AgentId=a.hyder&$page=1&$size=10  

**Agent Recruitment Project**

>  - It has the record of `Basic salary, Transportation, Housing, Food, CustomerID Customer Name, Project ID, Customer Project Name, Status, Arrival city, Departure city, Gender, Salary Identification, Customer Approval ID, Total number odf workers, Profession ID, Nationality ID and Other Allowances, etc.` Which the records are created by the ERP side and they call our integration api for create Recruitment Project api. 
>  - In the `Create form`, it includes the `identification, Customer Details, Salary, Travel, Application status and Selection.` 
>  - `Export` option is available to export the data or template in local and can Import in Bulk. These datas will refelct in application menu.

Create form **API -** https://portal.mawarid.com.sa/SystemApi/api/v1/categoryrequestertype?$page=1&$size=100&$filter:UserType=li:1 

## **Application**

  (In a General Sense) An interview application is a specialized software or platform designed to streamline and enhance the interview process across various contexts. Whether used for job interviews, research inquiries, or admissions evaluations, these applications offer a range of features to facilitate efficient and effective interactions. They often include tools for scheduling interviews, sending invitations, and conducting video interviews, especially in the era of remote work and virtual communication. With capabilities for recording, transcription, and analytics, interview applications contribute to improved data management and decision-making. These platforms aim to simplify collaboration among interviewers, customize interview formats, and integrate seamlessly with other systems, providing a comprehensive solution to optimize the entire interview lifecycle. 

![](./Assets/Application%20progressbar(AGP).png)

  While received an application, it will be filtered by stage by stage progressing.
  - **`"All"`** progress bar in Application menu represents the all of the applications that have been received to the agent.
  - **`"New"`** progress bar represents the New application which may receive recent application.
  - **`"Interview"`** progress bar lists the applicate, who are all going to attend an interview.
  - In **`"Selected"`** progress bar, it shows the filtered candidates from the previous "Interview" list, who are all selected in the interview.
  - In **`"Rejected"`** progress bar, it shows the filtered candidates from the "Interview" list, who are all rejected in the interview.
  - In **`"Stamped"`** progress bar, it shows the list of candidates who's applications and documents are verified and get stamped.
  - In **`"Cancelled"`** progress bar, it shows the list of candidates who's applications and documents are cancelled for any reasons valid.

>  - These Application datas are comes from 2 ways, one is from direct create in `Recruitment Project ERP` and another way is from export template and import in bulk from `Recruitment Project.` 
>  - To Create an Application, call api in application ERP and they return the ApplicationId, that we can save the ApplicationId.
>  - Any `Update or Create or File upload` is to be done only through the call event application.
>    
>  `Application ERP Create api` - {{System.FrameworkUrl}}api/v1/recruitment/CreateSelfServiceRequestERP
> 
>  `Application ERP Update api` - https://bcp.mawarid.com.sa/api/v1/erp/updateApplicationStatus
> 
>  `Application ERP File Upload (CV Attachment) api` - https://bcp.mawarid.com.sa/api/v1/erp/ExecuteApplicationAttachmentRequest 

## **API** 
  
  - Method - GET
  - URL -https://portal.mawarid.com.sa/SystemApi/api/v1/entitytype/dynamic/get/?entityTypeRecId=265&whereCondition={"Condtion":[{"FieldType":"FieldValue","Field":"agentAccount","Type":"Equal","Value":"Value","ValueTwo":"a.hyder"}]}&$page=1&$size=10&$filter:EnvironmentId=li:Live 

## **Interview**

  In a general sense, an interview is a formal interaction between two or more people, where one or more individuals (interviewers) ask questions and seek information from another person (interviewee). Interviews can take various forms and serve different purposes across different contexts, such as job interviews, journalistic interviews, research interviews, or informational interviews.

  1. **Job Interview:** This is perhaps the most common type of interview, where a candidate is assessed by potential employers to determine their suitability for a job position. The interviewers may ask about the candidate's qualifications, experience, skills, and assess their overall fit for the organization.

  2. **Journalistic Interview:** In journalism, interviews are conducted to gather information from individuals with knowledge or experience related to a particular topic. Journalists ask questions to obtain insights, quotes, or perspectives for news articles, features, or reports.

  3. **Research Interview:** Researchers use interviews as a method to collect data for studies. This can involve structured, semi-structured, or unstructured interviews, depending on the research goals. The researcher asks questions to understand the interviewee's experiences, opinions, or knowledge on a specific subject.

  4. **Informational Interview:** This type of interview is typically conducted by someone seeking career advice or information about a particular industry or job role. The interviewee is usually an experienced professional who shares insights and experiences to help the person seeking information.

![](./Assets/Interview%20progressbar(AGP).png)

  This Interview menubar has the agenda of the interview and seperated by progressing whether the scheduled interview has been completed or cancelled or rescheduled by date and time.

  - In **`"All"`** progress bar, it shows the all interview applications without any filtered data.

**API -** https://portal.mawarid.com.sa/SystemApi/api/v1//entitytype/dynamic/queryexecute?queryRecId=183&formRecId=11005&AgentId=a.hyder&$page=1&$size=10

  - **`"New"`** progress bar, it shows the recent new interview application which has been filtered from "All" progress bar.

**API -** https://portal.mawarid.com.sa/SystemApi/api/v1//entitytype/dynamic/queryexecute?queryRecId=183&formRecId=11006&whereCondition={"Condtion":[{"FieldType":"FieldValue","Field":"Status","Type":"Equal","Value":"Value","ValueTwo":"New"}]}&AgentId=a.hyder&Status=New&$page=1&$size=10

  - In **`"Scheduled"`** progress bar, it shows the scheduled interview application data which is filered from "All" progress bar.

**API -** https://portal.mawarid.com.sa/SystemApi/api/v1//entitytype/dynamic/queryexecute?queryRecId=183&formRecId=11007&whereCondition={"Condtion":[{"FieldType":"FieldValue","Field":"Status","Type":"Equal","Value":"Value","ValueTwo":"Scheduled"}]}&AgentId=a.hyder&Status=Scheduled&$page=1&$size=10

  - In **`"Completed"`** progress bar, it shows the completed interview data which is filtered from the previous "Scheduled" progress bar and the incompleted interview application will remains in the Scheduled list or in the cancelled list.

**API -** https://portal.mawarid.com.sa/SystemApi/api/v1//entitytype/dynamic/queryexecute?queryRecId=183&formRecId=11008&whereCondition={"Condtion":[{"FieldType":"FieldValue","Field":"Status","Type":"Equal","Value":"Value","ValueTwo":"Completed"}]}&AgentId=a.hyder&Status=Completed&$page=1&$size=10

  - In **`"Cancelled"`** progress bar, it shows the cancelled interview applications which is filtered from the previous "Completed" list or from the "Scheduled" list.

**API -** https://portal.mawarid.com.sa/SystemApi/api/v1/entitytype/dynamic/get/?entityTypeRecId=266&whereCondition={"Condtion":[{"FieldType":"FieldValue","Field":"Status","Type":"Equal","Value":"Value","ValueTwo":"Cancelled"}]}&$page=1&$size=10&$filter:EnvironmentId=li:Live

  - In **`"Rescheduled"`** progress bar, it shows the rescheduled interview applications. Whether the interview has been cancelled for any reasons, it can be rescheduled for another date and time. It is filtered from the previous "Cancelled" interview application list.  

**API -** https://portal.mawarid.com.sa/SystemApi/api/v1//entitytype/dynamic/queryexecute?queryRecId=183&formRecId=11590&whereCondition={"Condtion":[{"FieldType":"FieldValue","Field":"Status","Type":"Equal","Value":"Value","ValueTwo":"Reschedule"}]}&AgentId=a.hyder&Status=Reschedule&$page=1&$size=10

  - In **`"Backup"`** progress bar, it holds the backup data of the applicants who are all attend the interview.

**API -** https://portal.mawarid.com.sa/SystemApi/api/v1//entitytype/dynamic/queryexecute?queryRecId=183&formRecId=11591&whereCondition={"Condtion":[{"FieldType":"FieldValue","Field":"Status","Type":"Equal","Value":"Value","ValueTwo":"Backup"}]}&AgentId=a.hyder&Status=Backup&$page=1&$size=10

>  - In the Interview process, there is no `Import option.` 
>  - Only `Export option` is available to export data or a template.
>  - `Scheduled` interview data is get from the Application `Interview` by call event process.
>  - `Completed` - The shortlisted application has to update status in the `Selected` list in the Application stage by the call event process.
>  - `Completed` - The shortlisted application has to update status in the `Rejected` list in the Application stage by the call event process.
>  - ERP has been `Stamped` the shortlisted application and they call our integration api to update application status
> 
>  `Application Interview ERP Update api` - https://bcp.mawarid.com.sa/api/v1/erp/receiveInterviewLinkForApplication
> 
>  `Application Interview ERP Create api` - https://bcp.mawarid.com.sa/api/v1/erp/receiveInterviewScheduleForApplication


## **Flight Plan**

![](./Assets/Flight%20Plan%20progressbar(AGP).png)

  An Agent will record the details of a candidate's flight plan data for future reference, if an agent need. So he create a form to fill details of the selected candidate's flight plan after the interview process and selection process. In the Flight plan `Create form`, there was an information need to be fill about flight information which includes the `Agent name, Flight Id, Airline, Flight Number, Arrival airport, Arrival city, Project Id, Arrival date, Arrival time and Gender accomodation.` These informations also shows in both `Draft and Waiting for Arrival` progress bar. The agent will send off the selected candidates by the company's ticket. Those process of sending off selected applicants are called Flight plan. This flight plan process is differentiated by two progress. They are,

  1. Draft

  2. Waiting for arrival 

  **`Draft`** progress bar lists the selected applicants who are all in the waiting list which means yet to send off them.

  **`Waiting for Arrival`** progress bar shows the list of selected applicants who was confirmed their job with the flight ticket and soon to arrive for job. 

>  - While Creating the flight plan, call ERP api to get along with a `FlightPlanId` which is patched in oninit rules.
>  - Create a `Flight Plan` by the call event from ERP. We can create flight plan by two ways, call event from ERP is one and direct create in the flight plan page is an another way because, flight plan is a combined process of Agent and the Company.   

## **API** 
 
  - Method - GET
  - URL - https://portal.mawarid.com.sa/SystemApi/api/v1/entitytype/dynamic/get/?entityTypeRecId=270&whereCondition={"Condtion":[{"FieldType":"FieldValue","Field":"Status","Type":"Equal","Value":"Value","ValueTwo":"Draft"}]}&$page=1&$size=10&$filter:EnvironmentId=li:Live

Create form **API -** https://portal.mawarid.com.sa/SystemApi/api/v1/entitytype/dynamic/insert?appcode=App0000003&area=System&environmentcode=Live&user-id=a.hyder&username=a.hyder 

## **Flight Plan Line**

  Flight Plan Line holds the lists of Batch (Candidates), the batch which is assigned a  particular flights for a particular batch. It has a Candidate details and Flight details. The main part of the Flight Plan Line is to list the candidate's flight plan by batch who are all travel in the same flight.

>  - It reflects the `Stamped` application from the Application page.
>  - Call the required api to create `FlightPlan Line` ERP.   

## **API** 
 
  - Method - GET
  - URL - https://portal.mawarid.com.sa/SystemApi/api/v1/entitytype/dynamic/get/?entityTypeRecId=271&formRecId=11076&$page=1&$size=10&$filter:EnvironmentId=li:Live

## **API Collections**  

> [Click here](./Agent%20Portal%20API%20Collection.postman_collection.json) to view the API collections. In this collection, it has a full API collections of Agent Portal.

