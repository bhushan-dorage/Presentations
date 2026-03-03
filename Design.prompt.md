I am working on a workflow system design with name iQube V2. 
This system is built using multiple micro services.
It have following services 

1. Ingestion service - This service is config driven service. It uses a static data which is stored in DB table. This static data is a mapping between incoming data which may be in JSON or XML or CSV file from upstream system and the database table columns. These mapping would be json attribute path or XPath or CSV column name depending on data format. After mapping it stores the data in a business specific Case table.
It can integrate with upstream and downstream systems using REST or Kafka.

2. Workflow service - This service is a activiti based, it uses BPMN files to initiate a workflow. It provides a API to take actions on workflows. This service takes input as a event from Ingestion service. These inputs will be used to initiate new workflow and to generate a business_proc_id and update in the Case table or to claim task, or to complete a task or to assign the task to some user or to comment on task or to attach a file to business_process. 

3. Task service - This service will be used to create independent business tasks and mapping them with case.

4. Data view service - This service is used to fetch data from Case table and to show those to user on UI. It will have pagination support, sorting, filtering support. It will be also a config driven service. It will use case table columns names and display value mapping stored in Static table, it will also use data permissions like which data to show to user roles etc from static data config.

5. User action service - This service will provide APIs which will be called from UI. It would provide APIs to claim, assign, unassign, complete tasks, comment on task, attach file to task or business process etc. it will also have activiti integration.

6. Auth service - A LDAP based spring boot, spring security service which will be used for authentication and authorisation. It will also provide tokens for service to service authentication.

7. API gateway - it will be used for routing API requests which are originated from UI or from other services.

8. UI Service - An angular based UI Service which will show cases and tasks to users and provide features to take actions on Case and tasks.

Database tables:
1. Ingestion static table
2. Case table
3. Task table 
4. UI field and DB column mapping static table 
5. Data permissions table 
6. User roles tables 
7. Permissions table
8. User roles to permissions mapping table 

These services would be used as foundation set of services for any business specific use case. This set of services and DB tables would be deployed for each onboarded business usecase.

All the services would be implemented using Spring boot 

Database - PostgreSql 

Event streaming - Kafka 

Hosting - On premises Kubernetes 


Review this design and suggest improvements, I want this system to be high available, scalable, and performance.
 
Prepare a design document and diagrams for this platform.
