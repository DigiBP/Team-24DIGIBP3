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

He receives requests via various channels (WhatsApp, Instagram, SMS, email and so on). Customers contact him there and make an appointment with him. Customers also send him the necessary song files, with the audio tracks already recorded, via various channels. This is very time-consuming for him and also very confusing. In addition, he doesn't have a professional database of his customers and he also creates his invoices individually. He does this with the help of accounting software (Bexio), but this process is not automated either and has to be triggered and created manually.

Last but not least, the delivery of his finalized songs is not automated and he has to send them back to the customer manually via the channel through which he received the song file at the time.


### As-Is Process
@MIKAEL bitte ergänzen

### Project Goals
The goal of the project is to digitalize the order management process of mondetto's mixing offering. Right now he is not working automated nor fully digital.
To change this he needs an automated process, where his customers can fulfill an order. In this process they should be able the send their data, make a choice for the service they want and also be able to upload their songs, which they want to have mixed by mondetto. Afterwards it should be automated how the customer gets a notifaction and how mondetto can view the uploaded mixing request. 

@MIKAEL: bitte noch ergänzen dass neu auch Freelance involviert werden können.

## To-Be Process
@MIKAEL bitte übernehmen, erkläre den neuen Prozess. Bild von BPMN einfügen. 

### Overview Flow Steps
| Name                          | Type                | Short Description                                                                 | Details                          | 
|-------------------------------|---------------------|----------------------------------------------------------------------------------|----------------------------------|
| order request received        | Start Event         | When a new order is placed via form, process is started.                         | [Link](#order-request-received)  |
| check customer                | Service Task        | Checks in Bexio whether the Customer exists.                                     | [Link](#check-customer)          |
| customer existing?            | Exclusive Gateway   | Checks the result of check customer and controls token flow accordingly.         | [Link](#customer-existing)       |
| create customer               | Service Task        | In case the customer does not exist, a customer is created in Bexio.             | [Link](#create-customer)         |
| check capacity                | Service Task        | Verifies if there is enough capacity to fulfill the order.                       | [Link](#check-capacity)          |
| calculate total price        | Business Rule Task  | Computes the total price based on the order details.                             | [Link](#calculate-total-price)  |
| send offer                    | Service Task        | Sends the offer to the customer.                                                 | [Link](#send-offer)              |
| offer acceptance received     | Message Event       | Receives the offer acceptance from the customer.                                 | [Link](#offer-acceptance-received)|
| 12h deadline                  | Timer Event         | Waits for 12 hours to receive the offer acceptance.                              | [Link](#12h-deadline)            |
| request payment               | Service Task        | Sends a payment request to the customer.                                         | [Link](#request-payment)         |
| payment validation received   | Message Event       | Receives the payment validation from the payment gateway.                        | [Link](#payment-validation-received)|
| payment successful?           | Exclusive Gateway   | Checks if the payment was successful and controls token flow accordingly.        | [Link](#payment-successful)      |
| 2h deadline                   | Timer Event         | Waits for 2 hours to receive the payment validation.                             | [Link](#2h-deadline)             |
| cancel order                  | Service Task        | Cancels the order if payment is not received or unsuccessful.                    | [Link](#cancel-order)            |
| order cancelled               | End Event           | Ends the process if the order is cancelled.                                      | [Link](#order-cancelled)         |
| create invoice                | Service Task        | Creates an invoice for the order.                                                | [Link](#create-invoice)          |
| send order confirmation       | Send Task           | Sends an order confirmation to the customer.                                     | [Link](#send-order-confirmation) |
| calculate time for voucher compensation | Script Task        | Calculates the time needed for voucher compensation.                    | [Link](#calculate-time-for-voucher-compensation)|
| task initialized              | Start Event         | Indicates the start of the task initialization process.                          | [Link](#task-initialized)        |
| assign task                   | User Task           | Assigns the task to the appropriate personnel.                                   | [Link](#assign-task)             |
| task assigned to freelancer?  | Exclusive Gateway   | Checks if the task has been assigned to a freelancer.                            | [Link](#task-assigned-to-freelancer)|
| send task                     | Service Task        | Sends the task details to the assigned freelancer.                               | [Link](#send-task)               |
| receive task acceptance       | Receive Task        | Receives the task acceptance from the freelancer.                                | [Link](#receive-task-acceptance) |
| receive task completion       | Receive Task        | Receives the task completion notification from the freelancer.                   | [Link](#receive-task-completion) |
| 24h deadline                  | Timer Event         | Waits for 24 hours to receive the task completion.                               | [Link](#24h-deadline)            |
| control quality               | User Task           | Controls the quality of the completed task.                                      | [Link](#control-quality)         |
| adjustments needed?           | Exclusive Gateway   | Checks if any adjustments are needed for the completed task.                     | [Link](#adjustments-needed)      |
| mix song                      | User Task           | Mixes the song as part of the task process.                                      | [Link](#mix-song)                |
| task completed                | End Event           | Indicates that the task is completed.                                            | [Link](#task-completed)          |
| delivery date exceeded        | Timer Event         | Checks if the delivery date has been exceeded.                                   | [Link](#delivery-date-exceeded)  |
| create voucher                | Service Task        | Creates a voucher for the customer.                                              | [Link](#create-voucher)          |
| send voucher                  | Send Task           | Sends the voucher to the customer.                                               | [Link](#send-voucher)            |
| calculate adjustment requests left | Script Task    | Calculates how many adjustment requests are left for the task.                   | [Link](#calculate-adjustment-requests-left)|
| deliver mixed songs           | Service Task        | Delivers the mixed songs to the customer.                                        | [Link](#deliver-mixed-songs)     |
| 3 adaptions delivered?        | Exclusive Gateway   | Checks if 3 adaptions have been delivered.                                       | [Link](#3-adaptions-delivered)   |
| receive adjustment request    | Receive Task        | Receives an adjustment request from the customer.                                | [Link](#receive-adjustment-request)|
| adapt mix                     | User Task           | Adapts the mix based on the customer's request.                                  | [Link](#adapt-mix)               |
| order fulfilled               | End Event           | Indicates that the order has been fulfilled.                                     | [Link](#order-fulfilled)         |


## Implementation
Technical implementation

### Architecture
The Architecutre overview. 

### Process Variables
The Architecutre overview. 

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

## Outlook

#### adapt mix
Description

#### order fulfilled
Description
