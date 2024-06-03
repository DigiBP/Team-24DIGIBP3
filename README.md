# Team3 - Mondetto "mixing order management"
- [Team Members](#team-members%EF%B8%8F%EF%B8%8F%EF%B8%8F%EF%B8%8F) 
- [Coaches](#coaches) 
- [Introduction](#introduction)
  - [As-Is Process](#as-is-process)
  - [Project Goals](#project-goals)
- [To-Be Process](#to-be-process)
  - [Overview Flow Steps](#overview-flow-steps)
- [Implementation](#implementation)
  - [Architecture](#architecture)
  - [Process Variables](#process-variables)
  - [Flow Step Details](#flow-step-details)
- [Outlook](#outlook)


## Team Members👨🏻‍⚕️👨🏼‍⚕️👩🏻‍⚕️👨🏽‍⚕️
|Name|Email|
|----------|---------------|
|Elian Lüthy|elian.luethy@students.fhnw.ch|
|Hakan Bas|hakan.bas@students.fhnw.ch|
|Ismael Giosué Liuzzi|ismaelgiosue.liuzzi@students.fhnw.ch|
|Michael Christen|michael.christen1@students.fhnw.ch|


## Coaches
- Charuta Pande
- Andreas Martin


## Introduction
Mondetto is a swiss muscian and producer. He is an entrepreneur and works on different projects simultaneously. One service he offers is the finalizing (mixing and mastering) of songs. Recorded audio tracks are mixed together and various processes such as equalization (EQ), compression and reverb effects are used. At the moment, the whole process of creating an order for him is manual.

He receives requests via various channels (WhatsApp, Instagram, SMS, email and so on). Customers contact him there and make an appointment with him. Customers also send him the necessary song files, with the audio tracks already recorded, via various channels. This is very time-consuming for him and also very confusing. In addition, he doesn't have a professional database of his customers and he also creates his invoices individually. He does this with the help of accounting software (Bexio), but this process is not automated either and has to be triggered and created manually. Last but not least, the delivery of his finalized songs is not automated and he has to send them back to the customer manually via the channel through which he received the song file at the time.


### As-Is Process
In this chapter we briefly explain the as-is process. We have documented it in a BPMN as well, which is added below. Until now, the process is fully manual and nothing is automated.
Mondetto currently receives orders via various channels. This can be via WhatsApp, Instagram, email, etc. In these messages, customers also send him their song files, which they would like to have edited and mixed. When he accepts an order, he saves these files on a local drive. He then has to manually check whether the file is in the correct format and whether he can use it. Once this is done, he discusses the schedule for creating the mix with the customer. Again, this is done manually via a communication platform. Once he has all the necessary information, he can then begin his work. Until then, he loses valuable time during which he could already be mixing songs.

Now he can start with his actual work, the mixing. As soon as he has finished, he uploads the finished song file for the customer. He usually does this manually via Dropbox Premium. Sometimes, however, this is also done via WhatsApp, Instagram or a similar platform. He also informs the customer that their song file has been completed.
The customer can now check whether they are happy with it or whether they would like any further adjustments. He informs Mondetto of this via one of the aforementioned communication platforms. If the customer is not yet satisfied, Mondetto edits the song file again and the upload process including customer information is repeated. 

When the customer is satisfied with the song file, the invoice for the service is issued. He creates the invoice manually and then sends it to the customer by e-mail. He then has to enter the invoice in his Bexio accounting software. He also manages it there and can use it to record payments. This is important for his dunning process and for keeping proper accounts. But he still has to do this manually. Finally, he closes the order for himself and it is then completed. 

![As-is Model](https://github.com/DigiBP/Team-24DIGIBP3/blob/78ee0534811cd0ac4c58d37e8b95044916e23372/Pictures/As-is%20Mixing%20Order%20Management.png)


### Project Goals
The goal of the project is to digitalize the order management process of mondetto's mixing offering. Right now he is not working automated nor fully digital.
To change this he needs an automated process, where his customers can fulfill an order. In this process they should be able the send their data, make a choice for the service they want and also be able to upload their songs, which they want to have mixed by mondetto. Afterwards it should be automated how the customer gets a notifaction and how mondetto can view the uploaded mixing request.
Another pain point from the current process is, that Mondetto does not have an overview about his ongoing projects. This became a problem laltely, since his business has grown rapidly and he now also hires freelancers, who he can forward some tasks or projects to. This needs to be involved in the new process as well. He should be able to assign a song to one of the freelancers. Afterwards they can decide, if they want to accept the order or just ignore it. If they accept the job, they need to be able to send it back to Mondetto. Because he needs to verify every mixed song and check whether it meets its requirements. He may needs to adjust something before he sends it back to the customer.



## To-Be Process
To reach our project goals, the team had to create a completely new process and BPMN from the scratch. The full process is ad the end of this chapter.
First of all we had to discuss together with Mondetto, how he would like to have his future process and what is particularly important to him. 

### Receipt of the order
The first part of our process is the receipt of the order. We changed this completly. The process starts with the order request. This is triggered by a microsoft fomrs which the customer has to fill out. You can find the form in the [folder](https://github.com/DigiBP/Team-24DIGIBP3/blob/main/Microsoft%20Forms/Customer%20form%20for%20the%20mixing%20order%20request.pdf) or it is also directly available under the [link to forms](https://forms.office.com/e/q00ES47EVk).










![To-be Model](https://github.com/DigiBP/Team-24DIGIBP3/blob/78ee0534811cd0ac4c58d37e8b95044916e23372/Pictures/To-be-process%20Mixing%20Order%20Management.png)



### Overview Flow Steps

| Name                          | Type                | Short Description                                                                 | Details                          | 
|-------------------------------|---------------------|----------------------------------------------------------------------------------|----------------------------------|
| order request received        | Start Event         | When a new order is placed via form, process will be triggered                         | [Link](#order-request-received)  |
| check customer                | Service Task        | Checks in Bexio whether the Customer exists.                                     | [Link](#check-customer)          |
| customer existing?            | Exclusive Gateway   | Checks the result of check customer and controls token flow accordingly.         | [Link](#customer-existing)       |
| create customer               | Service Task        | In case the customer does not exist, a customer is created in Bexio.             | [Link](#create-customer)         |
| check capacity                | Service Task        | Verifies if there is enough capacity to fulfill the order.                      | [Link](#check-capacity)          |
| calculate total price        | Business Rule Task  | Computes the total price based on the order details.                             | [Link](#calculate-total-price)  |
| send offer                    | Service Task        | Sends an offer to the customer via HTML file in Email                           | [Link](#send-offer)              |
| offer acceptance received     | Message Event       | Receives the offer acceptance from the customer if customer clicked on accept   | [Link](#offer-acceptance-received)|
| 12h deadline                  | Timer Event         | Waits for 12 hours if it is reached it will cancel the order.                              | [Link](#12h-deadline)            |
| request payment               | Service Task        | Sends a payment request via Link in Email to the customer.                                         | [Link](#request-payment)         |
| payment validation received   | Message Event       | Receives the payment validation message .                        | [Link](#payment-validation-received)|
| payment successful?           | Exclusive Gateway   | Checks if the payment was successful and controls token flow accordingly.        | [Link](#payment-successful)      |
| 2h deadline                   | Timer Event         | Waits for 2 hours for payment validation if reached it will cancel the order                            | [Link](#2h-deadline)             |
| cancel order                  | Service Task        | Cancels the order and send info to the customer. Based on why cancellation was triggered, it sends different text.                    | [Link](#cancel-order)            |
| order cancelled               | End Event           | The process is cancelled due to order cancellation.                                      | [Link](#order-cancelled)         |
| create invoice                | Service Task        | Creates an invoice for the order on Bexio and creates PDF.                                                | [Link](#create-invoice)          |
| send order confirmation       | Send Task           | Sends the order confirmation via Email with Invoice PDF to the customer.                                     | [Link](#send-order-confirmation) |
| calculate time for voucher compensation | Script Task        | Calculates at what timestamp voucher compensation needs to be triggered.                    | [Link](#calculate-time-for-voucher-compensation)|
| task initialized              | Start Event         | For each Song a new task is initialized (parallel)                          | [Link](#task-initialized)        |
| assign task                   | User Task           | Mondetto either assign task to freelancer or own email.                                   | [Link](#assign-task)             |
| task assigned to freelancer?  | Exclusive Gateway   | Checks if the task has been assigned to a freelancer and controls token flow accordingly.                            | [Link](#task-assigned-to-freelancer)|
| send task                     | Service Task        | Sends the task details via HTML file in Email to the assigned freelancer and grants access to the raw song files.                               | [Link](#send-task)               |
| receive task acceptance       | Receive Task        | Waits for the task acceptance from the freelancer 12h deadline, otherwise Mondetto needs to perform mix.                                | [Link](#receive-task-acceptance) |
| receive task completion       | Receive Task        | Waits for the task completion notification from the freelancer.                   | [Link](#receive-task-completion) |
| 24h deadline                  | Timer Event         | Waits for 24 hours to receive the task completion, otherwise Mondetto need to perform mix.                               | [Link](#24h-deadline)            |
| control quality               | User Task           | Mondetto checks the quality of the mixed song from freelance and set if adjustments needed.                                      | [Link](#control-quality)         |
| adjustments needed?           | Exclusive Gateway   | Checks if any adjustments from Mondetto are needed for the song and controls token flow accordingly                     | [Link](#adjustments-needed)      |
| mix song                      | User Task           | Mondetto mixes the song with Audio Software & Plug-ins                                      | [Link](#mix-song)                |
| task completed                | End Event           | Indicates that the mixing of a song and therefore task is performed and done.                                            | [Link](#task-completed)          |
| delivery date exceeded        | Timer Event         | Checks if the delivery date has been exceeded and if so starts voucher creation.                                   | [Link](#delivery-date-exceeded)  |
| create voucher                | Service Task        | Creates a 20.- voucher for the customer for the circumstances and writes it in database.                                              | [Link](#create-voucher)          |
| send voucher                  | Send Task           | Sends the created voucher to the customer via Email.                                               | [Link](#send-voucher)            |
| calculate adjustment requests left | Script Task    | Calculates how many adjustment requests are left for the task. Inital 3 and afterwards decrease for each loop                   | [Link](#calculate-adjustment-requests-left)|
| deliver mixed songs           | Service Task        | Delivers the mixed songs to the customer via HTML file with buttons for adjustment request in Email, grants customer access rights to song file folder.                                        | [Link](#deliver-mixed-songs)     |
| 3 adaptions delivered?        | Exclusive Gateway   | Checks if 3 adjustments already have been delivered if yes process ends.                                       | [Link](#3-adaptions-delivered)   |
| receive adjustment request    | Receive Task        | Receives an adjustment request from the customer in text form.                                | [Link](#receive-adjustment-request)|
| adapt mix                     | User Task           | Adapts the mix based on the customer's request.                                  | [Link](#adapt-mix)               |
| order fulfilled               | End Event           | Indicates that the order has been fulfilled either after 3 adjustment round made or no feedback from customer for 3d.                                     | [Link](#order-fulfilled)         |


## Implementation
To implement the to-be process model and therefore to fulfill project goals we decided to rely on following architectural implementation.

### Architecture
![Architecture Overview](https://github.com/DigiBP/Team-24DIGIBP3/blob/78ee0534811cd0ac4c58d37e8b95044916e23372/Pictures/Architecture.png)

**Camunda:** With Camunda we steer the whole process token flow. A BPMN & DMN Model was deployed to the server. Mostly Camunda is using Service Tasks, which are calling via REST http  a Workflow deployed in Power Automate. If asynchronous answers are needed back, mainly messages were used that will be send by Power Automate or Buttons that are being clicked from Customer directly both via Camunda REST API. Mondetto will use Camunda to handle "Manual" User-Tasks. Freelancer or Clients will not have access to Camunda.
**Microsoft:** We decided to use the powerful capabilities of Microsoft for multiple purposes. For service integration we used Power Automate, for Email-correspondance Outlook, for Enter a new Mixing request MS Forms, for Data management of song files as well as a Voucher database we relied on SharePoint. 

**Bexio:** is a accounting tool and Mondetto is currently using it to manually enter invoices and managing customers. We used the bexio API https://docs.bexio.com/ to interact with customer database and handling invoices. 



### Process Variables
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


### Flow Step Details

#### order request received
Description

#### check customer
Description

#### customer existing?
Description

#### create customer
Description

#### check capacity
Description

#### calculate total price
Description

#### send offer
Description

#### offer acceptance received
Description

#### 12h deadline
Description

#### request payment
Description

#### payment validation received
Description

#### payment successful?
Description

#### 2h deadline
Description

#### cancel order
Description

#### order cancelled
Description

#### create invoice
Description

#### send order confirmation
Description

#### calculate time for voucher compensation
Description

#### task initialized
Description

#### assign task
Description

#### task assigned to freelancer?
Description

#### send task
Description

#### receive task acceptance
Description

#### receive task completion
Description

#### 24h deadline
Description

#### control quality
Description

#### adjustments needed?
Description

#### mix song
Description

#### task completed
Description

#### delivery date exceeded
Description

#### create voucher
Description

#### send voucher
Description

#### calculate adjustment requests left
Description

#### deliver mixed songs
Description

#### 3 adaptions delivered?
Description

#### receive adjustment request
Description

#### adapt mix
Description

#### order fulfilled
Description

## Outlook
