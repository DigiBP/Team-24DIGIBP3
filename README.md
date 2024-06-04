# Team3 - Mondetto "mixing order management" 🎚️🎛️
- [Team Members](#team-members-) 
- [Coaches](#coaches-) 
- [Introduction](#introduction-)
  - [As-Is Process](#as-is-process)
  - [Project Goals](#project-goals)
- [To-Be Process](#to-be-process-%EF%B8%8F)
  - [Business Perspective](#business-perspective)
  - [Flow Steps Overview](#flow-steps-overview)
- [Implementation](#implementation-)
  - [Architecture](#architecture)
  - [Process Variables](#process-variables)
  - [Flow Steps Details](#flow-steps-details)
- [Outlook](#outlook-)


## Team Members 👩‍🎓👨‍🎓
|Name|Email|
|----------|---------------|
|Elian Lüthy|elian.luethy@students.fhnw.ch|
|Hakan Bas|hakan.bas@students.fhnw.ch|
|Ismael Giosué Liuzzi|ismaelgiosue.liuzzi@students.fhnw.ch|
|Michael Christen|michael.christen1@students.fhnw.ch|


## Coaches 👩‍💼👨‍💼
- Charuta Pande
- Andreas Martin
  
*Thank you so much for the interesting lectures, your valuable inputs & the continous support!*


## Introduction 🎬🤝
Mondetto is a swiss muscian and producer. He is an entrepreneur and works on different projects simultaneously. One service he offers is the finalizing (mixing and mastering) of songs. This is where recorded audio tracks are mixed together and various processes such as equalization (EQ), compression and reverb effects are deployed. At the moment, the whole process of creating an order is manual. Neither he nor his customers can benefit from simple and automated mixing order management.

He receives requests via various communication channels and social media. Customers contact him there and make an appointment with him. Customers also send him there the necessary song files with their recorded audio tracks. This is very time-consuming for him and also very confusing. In addition, he doesn't have a professional database of his customers and he also creates his invoices individually. He does this with the help of the accounting software Bexio, but this process is not automated either and has to be triggered and created manually. Last but not least, the delivery of his finalized songs is not automated and he has to send them back to the customer manually via the channel through which he received the song file before.

Another pain point for him at the moment is that he can only forward his song files to partners in a very complicated way, if at all. Due to the growth of his business and the increasing demand for his services, he would like to regularly hire freelancers in the future who can do the work for him and also create mixings. They would be paid a flat rate and the mixings would always be checked and finalized by Mondetto at the end, so that the customer still has the “Mondetto label”.


### As-Is Process 
In this chapter we briefly explain the as-is process. We have documented it in a BPMN as well, which is added below. Until now, the process is fully manual and nothing is automated.
Mondetto currently receives orders via various channels. This can be via WhatsApp, Instagram, email, etc. In these messages, customers also send him their song files, which they would like to have edited and mixed. When he accepts an order, he saves these files on a local drive. He then has to manually check whether the file is in the correct format and whether he can use it. Once this is done, he discusses the schedule for creating the mix with the customer. Again, this is done manually via a communication platform. Once he has all the necessary information, he can then begin his work. Until then, he loses valuable time during which he could already be mixing songs.

Now he can start with his actual work, the mixing. As soon as he has finished, he uploads the finished song file for the customer. He usually does this manually via Dropbox Premium. Sometimes, however, this is also done via WhatsApp, Instagram or a similar platform. He also informs the customer that their song file has been completed.
The customer can now check whether they are happy with it or whether they would like any further adjustments. He informs Mondetto of this via one of the aforementioned communication platforms. If the customer is not yet satisfied, Mondetto edits the song file again and the upload process including customer information is repeated. 

When the customer is satisfied with the song file, the invoice for the service is issued. He creates the invoice manually and then sends it to the customer by e-mail. He then has to enter the invoice in his Bexio accounting software. He also manages it there and can use it to record payments. This is important for his dunning process and for keeping proper accounts. But he still has to do this manually. Finally, he closes the order for himself and it is then completed. 

![As-is Model](https://github.com/DigiBP/Team-24DIGIBP3/blob/main/Pictures/as_is_mondetto_mixing_order_management.png)


### Project Goals 
The goal of the project is to digitalize the order management process of mondetto's mixing offering. Right now he is not working automated nor fully digital.
To change this he needs an automated process, where his customers can fulfill an order. In this process they should be able the send their data, make a choice for the service they want and also be able to upload their songs, which they want to have mixed by mondetto. Afterwards it should be automated how the customer gets a notifaction and how mondetto can view the uploaded mixing request.
Another pain point from the current process is, that Mondetto does not have an overview about his ongoing projects. This became a problem laltely, since his business has grown rapidly and he now also hires freelancers, who he can forward some tasks or projects to. This needs to be involved in the new process as well. He should be able to assign a song to one of the freelancers. Afterwards they can decide, if they want to accept the order or just ignore it. If they accept the job, they need to be able to send it back to Mondetto. Because he needs to verify every mixed song and check whether it meets its requirements. He may needs to adjust something before he sends it back to the customer.



## To-Be Process ⚙️✅
To reach our project goals, the team had to create a completely new process and BPMN from the scratch. The full process is ad the end of this chapter.
First of all we had to discuss together with Mondetto, how he would like to have his future process and what is particularly important to him. 

### Business perspective
We would like to give you first, a comprehensive textual outline of the to-be process from a more business perspective. 

**Order request, payment and order confirmation** 

The first part of our process is the receipt of the order. We changed this completly. The process starts with the order request. This is triggered by a microsoft forms which the customer has to fill out.

Afterwards the data are forwarded to bexio and it checks, if there is already a customer with this e-mail address. If not, there is automatically a new customer created in bexio. The next step is a check, weather Mondetto has some capacity to fullfill the order. If not, the order will be cancelled and the the process ends there.

When there is some capacity, the next step is to calculate the price of the services. There it depends, which service type (express, advanced or basic) and which amount of songs (one to five) the customer has choosen in his order request in forms. In the price calculation is also the option of a voucher included (customers can get vouchers from Mondetto for example if he is delayed with his delivery). When the price is calculated, the system sends an offer via e-mail to the customer. He has 12 hours to accept it via a link. If he does not do so within this time, the order is canceled and the process ends. If he confirms via the link within this time, a payment request is automatically triggered and the customer receives another e-mail with payment link. The services are always paid in advance. After the payment has been validated, an invoice is generated in Bexio and an order confirmation with the invoice/payment confirmation is sent to the customer by e-mail.

**Mixing task**

Only now Mondetto's task begins. He checks the order and decides whether to carry out the job himself or assign it to one of his freelancers. If he takes it on himself, he starts mixing and as soon as he has finished, his task is complete. If he forwards the order to a freelancer, the freelancer receives the order by e-mail. The freelancer in turn has 12 hours to accept the job. If this does not happen, Mondetto mixes the song himself. Otherwise, the process waits until the freelancer has finished the job and then passes the song on to Mondetto for a quality check. If, in his opinion, adjustments are necessary, he makes them immediately. The task is then completed. If the delivery time for the whole order is exceeded (delivery date is over), a voucher is automatically created for the customer and sent directly to them by e-mail.

**Adjustments** 

After the mixing task has been completed, the songs are delivered to the customer. They can download and check the songs using the provided SharePoint link. If the customer is satisfied with the song, he does not have to do anything else and the process is automatically be completed after 3 days and the order is thus fulfilled. However, if the customer wants to make adjustments to the song, he must report this within 3 days. In this case, Mondetto adjusts the song respective the comment from the customer and uploads the new file to Sharepoint again for the customer. The customer can request an adjustment 3 times. After the 3rd time, the order is directly fullfilled and the process is completed.

### BPMN model
![To-be Model](https://github.com/DigiBP/Team-24DIGIBP3/blob/78ee0534811cd0ac4c58d37e8b95044916e23372/Pictures/To-be-process%20Mixing%20Order%20Management.png)



### Flow Steps Overview 
Below you find an overview of all Flow components that were used in the shown BPMN model. For mroe complex steps details can be found via link to the Implementation chapter. 

| Name                          | Type                | Short Description                                                                 | further Details                          | 
|-------------------------------|---------------------|----------------------------------------------------------------------------------|----------------------------------|
| order request received        | Start Event         | When a new order is placed via form, process will be triggered                         | [Link](#order-request-received)  |
| check customer                | Service Task        | Checks in Bexio whether the Customer exists.                                     | [Link](#check-customer)          |
| customer existing?            | Exclusive Gateway   | Checks the result of check customer and controls token flow accordingly.         | -     |
| create customer               | Service Task        | In case the customer does not exist, a customer is created in Bexio.             | [Link](#create-customer)         |
| check capacity                | Service Task        | Verifies if there is enough capacity to fulfill the order.                      | [Link](#check-capacity)          |
| calculate total price        | Business Rule Task  | Computes the total price based on the order details.                             | [Link](#calculate-total-price)  |
| send offer                    | Service Task        | Sends an offer to the customer via HTML file in Email                           | [Link](#send-offer)              |
| offer acceptance received     | Message Event       | Receives the offer acceptance from the customer if customer clicked on accept   | [Link](#offer-acceptance-received)|
| 12h deadline                  | Timer Event         | Waits for 12 hours if it is reached it will cancel the order.                              | -           |
| request payment               | Service Task        | Sends a payment request via Link in Email to the customer.                                         | [Link](#request-payment)         |
| payment validation received   | Message Event       | Receives the payment validation message .                        | [Link](#payment-validation-received)|
| payment successful?           | Exclusive Gateway   | Checks if the payment was successful and controls token flow accordingly.        | -   |
| 2h deadline                   | Timer Event         | Waits for 2 hours for payment validation if reached it will cancel the order                            | -          |
| cancel order                  | Service Task        | Cancels the order and send info to the customer. Based on why cancellation was triggered, it sends different text.                    | [Link](#cancel-order)            |
| order cancelled               | End Event           | The process is cancelled due to order cancellation.                                      | -       |
| create invoice                | Service Task        | Creates an invoice for the order on Bexio and creates PDF.                                                | [Link](#create-invoice)          |
| send order confirmation       | Send Task           | Sends the order confirmation via Email with Invoice PDF to the customer.                                     | [Link](#send-order-confirmation) |
| calculate time for voucher compensation | Script Task        | Calculates at what timestamp voucher compensation needs to be triggered.                    | -|
| task initialized              | Start Event         | For each Song a new task is initialized (parallel)                          | -     |
| assign task                   | User Task           | Mondetto either assign task to freelancer or own email.                                   | [Link](#assign-task)             |
| task assigned to freelancer?  | Exclusive Gateway   | Checks if the task has been assigned to a freelancer and controls token flow accordingly.                            |- |
| send task                     | Service Task        | Sends the task details via HTML file in Email to the assigned freelancer and grants access to the raw song files.                               | [Link](#send-task)               |
| receive task acceptance       | Receive Task        | Waits for the task acceptance from the freelancer 12h deadline, otherwise Mondetto needs to perform mix.                                | [Link](#receive-task-acceptance) |
| receive task completion       | Receive Task        | Waits for the task completion notification from the freelancer.                   | [Link](#receive-task-completion) |
| 24h deadline                  | Timer Event         | Waits for 24 hours to receive the task completion, otherwise Mondetto need to perform mix.                               | -            |
| control quality               | User Task           | Mondetto checks the quality of the mixed song from freelance and set if adjustments needed.                                      | [Link](#control-quality)         |
| adjustments needed?           | Exclusive Gateway   | Checks if any adjustments from Mondetto are needed for the song and controls token flow accordingly                     | -      |
| mix song                      | User Task           | Mondetto mixes the song with Audio Software & Plug-ins                                      | [Link](#mix-song)                |
| task completed                | End Event           | Indicates that the mixing of a song and therefore task is performed and done.                                            | -        |
| delivery date exceeded        | Timer Event         | Checks if the delivery date has been exceeded and if so starts voucher creation.                                   | - |
| create voucher                | Service Task        | Creates a 20.- voucher for the customer for the circumstances and writes it in database.                                              | [Link](#create-voucher)          |
| send voucher                  | Send Task           | Sends the created voucher to the customer via Email.                                               | [Link](#send-voucher)            |
| calculate adjustment requests left | Script Task    | Calculates how many adjustment requests are left for the task. Inital 3 and afterwards decrease for each loop                   | -|
| deliver mixed songs           | Service Task        | Delivers the mixed songs to the customer via HTML file with buttons for adjustment request in Email, grants customer access rights to song file folder.                                        | [Link](#deliver-mixed-songs)     |
| 3 adaptions delivered?        | Exclusive Gateway   | Checks if 3 adjustments already have been delivered if yes process ends.                                       | -  |
| receive adjustment request    | Receive Task        | Receives an adjustment request from the customer in text form.                                | [Link](#receive-adjustment-request)|
| adapt mix                     | User Task           | Adapts the mix based on the customer's request.                                  | [Link](#adapt-mix)               |
| order fulfilled               | End Event           | Indicates that the order has been fulfilled either after 3 adjustment round made or no feedback from customer for 3d.                                     | -      |


## Implementation 📡🧩
To implement the to-be process model and therefore to fulfill project goals we decided to rely on following architectural implementation.

### Architecture
**Camunda:** With Camunda we steer the whole process token flow. A BPMN & DMN Model was deployed to the [server](https://digibp.herokuapp.com/engine-rest). Mostly Camunda is using Service Tasks, which are calling via a HTTP call a Workflow deployed in Power Automate. If asynchronous answers are needed back, mainly messages were used that will be sent by Power Automate or Buttons that are being clicked from Customer directly both via Camunda REST API Message calls. Mondetto will use Camunda to handle "Manual" User-Tasks. Freelancer or Clients will not have access to Camunda.

**Microsoft:** We decided to use the powerful capabilities of Microsoft for multiple purposes. We created a completely new Microsoft tenant (mondetto.onmicrosoft.com) so we could steer all Admin settings without interfearing the current set-up from Mondetto. We created 5 Users that all have a Power Plattform Premium and a Microsoft E3 License. *If you want to access any of the Microsoft ressources please use the log-ins, provided in the submission.* 
We used following components of Microsoft:

- **PowerAutomate** for complete service integration we used Power Automate. We developped our cloud flows in one solution which can be found exported in the files of this site or via [this link](https://make.powerautomate.com/environments/Default-13e90b05-c0bc-4500-971d-862a31887574/solutions/c73e4be0-9c1b-ef11-840b-00224860decf). Most of the developed flows are being triggered by a HTTP call from the running process via Camunda's service tasks. Then the flow steps are being executed and a response is being sent back. An explanation of the executed steps in the flow can be found in Flow Steps Detail chapter. To see the steps within a flow, please click on the respective flow and click on edit (left upper corner). 

- **Forms** for entering a new Mixing request Form by a customer. You can find the screenshots of the form in the [folder](https://github.com/DigiBP/Team-24DIGIBP3/blob/main/Microsoft%20Forms/Customer%20form%20for%20the%20mixing%20order%20request.pdf) or it is also directly available under the [link to forms](https://forms.office.com/e/q00ES47EVk). The Form is currently only accesible for mondetto.onmicrosoft.com internal users and will be made public later in go-live of solution. 

- **SharePoint** We created the SharePoint site: https://mondetto.sharepoint.com/sites/DigiBP/ for multiple purposes. We used [document library](https://mondetto.sharepoint.com/sites/DigiBP/Shared%20Documents/Forms/AllItems.aspx) for the management of the song & invoice files. Furthemore we used a SP-List as our [Voucher database](https://mondetto.sharepoint.com/sites/DigiBP/Lists/VoucherList/AllItems.aspx).

- **Outlook** for Email-correspondance with customer and freelancer. Mostly a HTML composed email is being sent and in addition a HTML file attached is also being send as in email html most providers do not allow java-script code, that are necessary for the process.  

**Bexio:** is a accounting tool and Mondetto is currently using it to manually enter invoices and managing customers. We used the bexio API https://docs.bexio.com/ to interact with customer database and handling invoices. Therefore a test tenant was implemented to not interfere with the real customer data / invoices from Mondetto. The log-in to that account can be found in the submission. In all Bexio API calls a header with a authorization token is being sent. 

![Architecture Overview](https://github.com/DigiBP/Team-24DIGIBP3/blob/78ee0534811cd0ac4c58d37e8b95044916e23372/Pictures/Architecture.png)




### Process Variables
The following process variables were being used in Camunda. The variables can have different initialization sources: 1. In Camunda directly by (manual user) input, calculation (DMN) or script tasks. 2. By HTTP responses from a Service Task (Power Automate). By receiving a variable loaded message sent to the process instance.   

| FieldName               | Type    | Description                                                | Example / Potential Values |
|-------------------------|---------|------------------------------------------------------------|-----------------------------|
| AdjustmentDescription   | String  | What does the customer want to have adjusted in the next version | too bass intensive     |
| AdjustmentNeeded        | Boolean | LOCAL variable: if after freelancers' work adjustments are needed | TRUE                        |
| AdjustmentRequestsLeft  | Integer | How many adjustments does the customer have left           | 2                           |
| AssignedTo              | String  | LOCAL variable: if assigned to a freelancer, to whom       | test@hotmail.com            |
| CapacityExisting        | String  | Shows if capacity is existing or not                       | yes, no                     |
| CustomerAddress         | String  | The address of a customer                                  | Aarepark 5a                 |
| CustomerCity            | String  | The city of a customer                                     | Aarau                       |
| CustomerEmail           | String  | The email of a customer                                    | john.doe@email.de           |
| CustomerExisting        | Boolean | Is the customer an existing one?                           | TRUE                        |
| CustomerFirstName       | String  | The first name of a customer                               | Max                         |
| CustomerID              | String  | ID from Customer in Bexio                                  | 123                         |
| CustomerLastName        | String  | The last name of a customer                                | Mustermann                  |
| CustomerPLZ             | String  | The PLZ of a customer                                      | 5000                        |
| Deadline                | String  | LOCAL variable: shows until when the freelancer has time to perform mixing | 2022-03-11T12:13:14Z        |
| DeliveryDate            | String  | The date when the song needs to be delivered               | yyyy-MM-dd => 2023-04-18    |
| FilesURL                | String  | URL to the folder                                          | htttp://www.google.com      |
| FormattedDeliveryDate   | String  | Delivery date plus one day, as then a voucher needs to be sent | 2022-03-11T12:13:14Z        |
| InvoiceID               | String  | The ID of an invoice                                       | 5 or 3 or 3333....          |
| OfferSent               | String  | Shows if an offer is being sent                            | yes, no                     |
| OrderID                 | String  | The ID of an order (also the business key of process instance) | 4 or 1 or 2222....          |
| PaymentRequested        | String  | Shows if payment is requested                              | yes, no                     |
| PaymentStatus           | String  | Shows payment status                                       | Succeeded                   |
| ServiceType             | String  | Which service type did the customer select?                | Basic, Advanced, Express    |
| SongID                  | String  | LOCAL variable: Name or ID of a song                       | Love, 1, 2                  |
| SongsAmount             | Integer | How many songs does the customer want to be mixed?         | 2                           |
| total_price             | Integer | Total price of the order                                   | 150                         |
| VoucherAmount           | Integer | Amount of voucher that can be deducted                      | 200                         |
| VoucherID               | String  | The ID from the voucher in the voucher list                 | FALSE                       |


### Flow Steps Details

#### order request received
To initialize the process, the Customer fills out the previously shown form. An automated cloud flow is waiting for a new response of this form and is being triggered by that. The Response ID from forms will build the OrderID/Business Key 

1. the flow gets then all response details
2. all files that were uploaded are being transfered to a freshly created, order dedicated folder
3. the flow checks which service type have been selected and sets the variable correctly and calculates the delivery date
4. if the user has handed in a voucher code, this voucher code is being checked and searched for an existing valid voucher with the same code in the SP-List. If it finds a voucher it will set the value of how much can be deducted later and hands-over the ID of the Voucher so in case the customer really pays, the voucher can be set invalid.
5. A HTTP Message is being sent to Camunda REST API to initialize a process instance and with all relevant variables as POST to https://digibp.herokuapp.com/engine-rest/process-definition/key/#ProcessID/tenant-id/24DIGIBP3/submit-form it uses a environment variable in the URL so in case of ProcessID changes this can easily be changed in all flows. 

[Link to Flow on Power Automate](https://make.powerautomate.com/environments/Default-13e90b05-c0bc-4500-971d-862a31887574/solutions/c73e4be0-9c1b-ef11-840b-00224860decf/flows/c3648a77-7272-430e-957c-1eceff210af6/details?utm_source=solution_explorer)

#### check customer
Camunda sends HTTP request to [this URL](https://prod2-21.switzerlandnorth.logic.azure.com:443/workflows/2f83c0d9d18e4b1e8ee2996e7e324349/triggers/manual/paths/invoke?api-version=2016-06-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=kBPgYW7eUNmhXXXHrS3e24mvnNH7wMBMYbbA5H6f84s) trigger the workflow and submitts all variables in the body. The flow is executing following steps: 

1. It calls the Bexio API GET https://api.bexio.com/2.0/contact
2. for each contact Object that bexio reutrns: the flow checks if the email in Bexio is the same as the CusotmerEmail from the Customer.
3. If yes it sends back to Camunda as response the ID of the customer and that CustomerExisting is true.
4. If not no ID is being send and CustomerExisting is false

[Link to Flow on Power Automate](https://make.powerautomate.com/environments/Default-13e90b05-c0bc-4500-971d-862a31887574/solutions/c73e4be0-9c1b-ef11-840b-00224860decf/flows/edd8b75e-e889-4be9-aa88-6cd72502ff96/details?v3=false)

#### create customer
Camunda sends HTTP request to [this URL](https://prod2-01.switzerlandnorth.logic.azure.com:443/workflows/65e965b9bc794848a0ca7c9fc0f5222d/triggers/manual/paths/invoke?api-version=2016-06-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=YyycdWWkIwS63tphJN8CGtIj0cX_N1ML_xOUiu7lwvo) to trigger the workflow and submitts all variables in the body. The flow is executing following steps:

1. Calls Bexio API as POST to https://api.bexio.com/2.0/contact in the body all relevant values ae handed over that were fetched from the trigger send from Camunda
2. Responses back to Camunda the CustomerID that was retrieved from Bexio as a response from previous call

[
Link to Flow on Power Automate](https://make.powerautomate.com/environments/Default-13e90b05-c0bc-4500-971d-862a31887574/solutions/c73e4be0-9c1b-ef11-840b-00224860decf/flows/0f37b0dd-27bd-4a88-936a-63319fe12d1a/details?utm_source=solution_explorer)

#### check capacity
Camunda sends HTTP request to [this URL](https://prod2-15.switzerlandnorth.logic.azure.com:443/workflows/f86c41434b9d48f8a90271379cbfbf5e/triggers/manual/paths/invoke?api-version=2016-06-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=ohzm2rQiD_iyfj39tlexCgF60C0H8KeJUPX9ahCfRFo) to trigger the workflow and submitts all variables in the body. The workflow will currently always send back that capacity is exsiting. This Service could later be implemented by using access to the calendar of Mondetto and evaluates if Capacity is really existing for the given order request. 

[Link to Flow on Power Automate](https://make.powerautomate.com/environments/Default-13e90b05-c0bc-4500-971d-862a31887574/solutions/c73e4be0-9c1b-ef11-840b-00224860decf/flows/06df68ab-6307-4325-bec9-93e3973ac889/details)

#### calculate total price
The total price is calculated in this step. A DMN is used for it. The DMN is using the ServiceType, VoucherAmount and the SongsAmount to calculate. The mores songs that are being requested the cheaper the rate per song gets. The ServiceTypes have different rates. The VoucherAmount is always being deducted. total_price is the outcome variable of this step. 

#### send offer
Camunda sends HTTP request [to this URL](https://prod2-11.switzerlandnorth.logic.azure.com:443/workflows/85f2f10b084440edaca3f318ce1667fc/triggers/manual/paths/invoke?api-version=2016-06-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=MwXCmV6KKrkGzc9wmY25553nFhTqefpsZOhdb2hM5NM) to trigger the workflow and submitts all variables in the body. The flow is executing following steps:

1. There is a HTML file being composed. This HTML file is showing the offer details like price etc. In this file there is also a button to accept the offer. If the Customer is clicking the button a  java-script is being activated that sends the "OfferAcceptanceReceived" messagewith the business key to Camunda, https://digibp.herokuapp.com/engine-rest/message. After clicking the button Customer will see if his accept was successfull (in case 200 response from Camunda) or if there was an error (e. g. 12h deadline over)
2. A Mail is being sent to the customer styled in HTML, to announce the offer. In the attachement the previous explained HTML file will be sent.
3. The flow sends back Response to Camunda with body to set var OfferSent to yes.   

[Link to Flow on Power Automate](https://make.powerautomate.com/environments/Default-13e90b05-c0bc-4500-971d-862a31887574/solutions/c73e4be0-9c1b-ef11-840b-00224860decf/flows/4b942f63-9917-49d5-96df-4f4d17bfa1f0/details?utm_source=solution_explorer)

#### offer acceptance received
As written in the previous step "send offer" the OfferAcceptanceReceived Message will being sent by clicking on the button in the HTML in attachment of the mail.

#### request payment
Camunda sends HTTP request to [this URL](https://prod2-07.switzerlandnorth.logic.azure.com:443/workflows/b66ce851067a4fcbae796bf12d54e90c/triggers/manual/paths/invoke?api-version=2016-06-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=0FCkiLBk3Cd0SkzfSVG-iWUK7z4S1DMf9RzmfyI6uN0) to trigger the workflow and submitts all variables in the body. The flow is executing following steps:

1.It composes the HTML email body. In the body there is a payment link included. This link is actuallly contatining a link to again call another workflow on Power Automate (see next step). In the link the OrderID and the Total price are handed over by using relative path and not in the body. The Link: "https://prod2-07.switzerlandnorth.logic.azure.com/workflows/cf843286559d4e51a72bfd5d0f3ddb3c/triggers/manual/paths/invoke/orders/['OrderID']/['total_price']?api-version=2016-06-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=ByuYr3yJIUYNdzCb_ZsFhZINFEC1gtR2MCR9jVCGzKU
2. It sends the Email to the customer with the previously composed body. 
3. The workflow sends a response to Camunda var PaymentReuqested set to yes

Of course this is only a simulation of a payment in real life we would include payment provider.

[Link to Flow on Power Automate](https://make.powerautomate.com/environments/Default-13e90b05-c0bc-4500-971d-862a31887574/solutions/c73e4be0-9c1b-ef11-840b-00224860decf/flows/2f49a34f-1631-48f8-a5f3-0e23aef10a3e/details?utm_source=solution_explorer)

#### payment validation received
Once the Customer clicks on the link of the previous step, automatically this flow is executing following steps:

1. It reads from the link's relative path (/orders/{OrderID}/price/{total_price})  for which order the payment was suceeded.
2. This OrderID is then being taken to post a message to Camunda and writes var PaymentStatus as Succeeded
3. As as response to this URL call from the User by clicking the payment link, a response is being sent with content-type text/html. So the users sees the confirmation of the payment in his opened browser tab. 


[Link to Flow on Power Automate](https://make.powerautomate.com/environments/Default-13e90b05-c0bc-4500-971d-862a31887574/solutions/c73e4be0-9c1b-ef11-840b-00224860decf/flows/8110fcf6-83e6-4e2b-b714-a59ad26176d9/details?utm_source=solution_explorer)

#### cancel order
Camunda sends HTTP request to [this URL](https://prod2-31.switzerlandnorth.logic.azure.com:443/workflows/f073a21ea1e74361b3dcd4f1bcf9dd18/triggers/manual/paths/invoke?api-version=2016-06-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=lf0hIs6AThh0iQF9E7GZOkGPoIDwp_gqxTUjC_24jBY) to trigger the workflow and submitts all variables in the body. This service tasks can be executed in 3 cases: 1. no capacity, 2. Customer is not accepting offer, 3. Order is not paid. The flow is executing following steps:

1. A CancellationReason variable is being set. Per default the value is set to Technical Issues.
2. It performs three Condition checks to find out why the order has been cancelled. Therefore it checks the variable values of following process variables: Capcity, PaymentRequested, PaymentStatus. One of the conditon should be true so, it sets the Reason of cancellation accordingly.
3. An email body is being composed in HTML with the reason included
4. A success response is being sent to Camunda

[Link to Flow on Power Automate](https://make.powerautomate.com/environments/Default-13e90b05-c0bc-4500-971d-862a31887574/solutions/c73e4be0-9c1b-ef11-840b-00224860decf/flows/c9409310-18e7-43e7-9ff3-4014072da53a/details?utm_source=solution_explorer)

#### create invoice
Camunda sends HTTP request to [this URL](https://prod2-25.switzerlandnorth.logic.azure.com:443/workflows/c07e15682bfd4cad880031ed80e620ec/triggers/manual/paths/invoke?api-version=2016-06-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=O51k_vLPh4Ph3w0o5vYCSK4Z6Cw8rPLJqO0UyszaH48) to trigger the workflow and submitts all variables in the body. The flow is executing following steps:

1. Bexio API https://api.bexio.com/2.0/kb_invoice is being called to create a invoice. All relevant parameteres in the json body are being filled with the process variables.
2. Bexio API https://api.bexio.com/2.0/kb_invoice/['id']/issue is being called. The ID in the URI is being automatically set by the InvoiceID that is being retrieved from previous step. This Call will issue the invoice which is mandatory for next step.
3. Bexio API https://api.bexio.com/2.0/kb_invoice/['id']/payment is being called. Again ID is fetched from output from step one. By that a payment is being recorded. As we are using pre payment always the whole total is being set as paid.
4. Bexio API https://api.bexio.com/2.0/kb_invoice/['id']/pdf is being called. Again ID is fetched from output from step one. This call will return a base64 encoded Invoice PDF file.
5. The base64 encoded is being decoded
6. An invoice file is being created on SP with correct naming.
7. A child flow is being called for sending the order confirmation (see next flow step)
8. If a voucher was used and deducted from the total, this voucher needs to be set to invalid in sharepoint. This step can fail if there is no voucher used, this is catched in scope and flow is anyway executing next step.
9. A success response is being sent to Camunda ith the InvoiceID in body

[Link to Flow on Power Automate
](https://make.powerautomate.com/environments/Default-13e90b05-c0bc-4500-971d-862a31887574/solutions/c73e4be0-9c1b-ef11-840b-00224860decf/flows/926528cd-e972-470b-bbc3-d9c34ad0aa31/details?utm_source=solution_explorer)

#### send order confirmation
Thiss step is a Send Task in camunda which is not further implemented there. It is actually being called by the previously shown cloud flow that calls this child flow with several Input Parameters that the child flow do need. This child flow is performing following steps: 

1. It gets the Invoice file content from SharePoint
2. it composes a nice Email HTML body to send the order confiration
3. it sends an email to the customer with the invoice attached (payment confirmation)

[Link to Flow on Power Automate
](https://make.powerautomate.com/environments/Default-13e90b05-c0bc-4500-971d-862a31887574/solutions/c73e4be0-9c1b-ef11-840b-00224860decf/flows/62bbb594-147d-4dc8-adba-9e8152e92510/details?utm_source=solution_explorer)

#### assign task
For each song that needs to be mixed a task is being created in the tasklist of Camunda. Mondetto now needs to decide if he or a Freelancer should perform the mixing for this specific song. He needs to claim the task and type in for which song this task is typing in SongName or ID in the field. If he uses his email "digibpgroup3@mondetto.onmicrosoft.com" in the assignedTO field, he has to mix the task otherwise the task will be sent to the handed-in email address. 


#### send task
Camunda sends HTTP request to [this URL](https://prod2-09.switzerlandnorth.logic.azure.com:443/workflows/ee2fc059884c4654960521765a876e55/triggers/manual/paths/invoke?api-version=2016-06-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=oDJcyzb2lImB_0VkT0a_j6s589kH20WjCWMRoPI7AiQ) to trigger the workflow and submitts all variables in the body. The flow is executing following steps:


1. The Folder metadata from the folder which includes the songfiles is being gotten by OrderID in the path
2. As an outcome of the previous step we have the FolderID and can therefore grant in this step view rights to the files to the person in the assignedTo field
3. A HTML file is being composed. This HTML file is showing the task details like which Song, Compensation (60.-) etc. In this file there is two buttons one to accept the task offer and the other to mark the task as completed. If the freelance later is clicking the accept task offer button a java-script is being activated that sends the "ReceiveTaskAcceptance" message with the to Camunda; if the freelance later is clicking the completed task button again a java-script is being activated that sends the "ReceiveTaskCompletion" message to Camunda. See more details in next flow steps chaptor. After clicking the buttons Customer will see if it was successfull (in case 200 response from Camunda) or if there was an error. 
4. A Mail is being sent to the freelancer styled in HTML, to announce the offer. In the attachement the previous explained HTML file will be sent.
5. The flow sends back Response to Camunda

[Link to Flow on Power Automate](https://make.powerautomate.com/environments/Default-13e90b05-c0bc-4500-971d-862a31887574/solutions/c73e4be0-9c1b-ef11-840b-00224860decf/flows/11442929-8626-4a13-80db-7421e42be9e6/details?utm_source=solution_explorer)

#### receive task acceptance
This message is being received because the Freelancer pressed the first button from previous flow step. In the previous sent messages the BusinessKey has always been sent as the unique identfier to find the correct token that is waiting for the message. 

 https://digibp.herokuapp.com/engine-rest/message



#### receive task completion
Camunda sends HTTP request to this URL to trigger the workflow and submitts all variables in the body. The flow is executing following steps:

Link to Flow on Power Automate

#### control quality
Description


#### mix song
Description



#### create voucher
Camunda sends HTTP request to this URL to trigger the workflow and submitts all variables in the body. The flow is executing following steps:

Link to Flow on Power Automate

#### send voucher
Description

Link to Flow on Power Automate

#### deliver mixed songs
Camunda sends HTTP request to this URL to trigger the workflow and submitts all variables in the body. The flow is executing following steps:

Link to Flow on Power Automate

#### receive adjustment request
Description

Link to Flow on Power Automate

#### adapt mix
Camunda sends HTTP request to this URL to trigger the workflow and submitts all variables in the body. The flow is executing following steps:


## Outlook 🔭🔮
The fact that we worked very closely with Mondetto throughout the project means that our solution is practically tailor-made for him. He was able to bring in all his needs and we created the process individually according to his wishes. We also made sure that it was feasible for him. 
We have already presented the project to Mondetto and he is delighted. He wants to implement the new version of his mixing order management process as soon as possible. To do this, he first needs to purchase a Microsoft 365 business license. This gives him access to all the tools he needs, such as PowerAutomate, Microsoft Forms, Sharepoint, etc. In addition, he must have access to Camunda or another tool for steering processes. Our team will then implement the process so that Mondetto will soon be able to use the automated mixing order management process. We have also calculated the monthly costs for him, if he wants to implement our project. There will be estimated costs of about CHF 70.- per month. He is sure that this is definitely worth it and the investment would be profitable, as the new process allows him to scale up the mixing business, with the integration of freelancers.
