---
title: Cancel
keywords: activities, data structure, cancel
sidebar: mydoc_sidebar
permalink: /docs/activities/DSF/cancel
---



### Method Goals


This method aims to cancel a booking



### Request Format


The request requires the booking code and the name of the customer



### Response Format


The result returns the new status of the reservation and the possible
cost of the cancellation.



### Remarks


Not implemented by all suppliers



### CancelRQ Example



~~~xml
    <OTA_TourActivityCancelRQ xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" PrimaryLangID = "es">
      <Confirmation ID="1283479#1" type="PROVIDER" />
    </OTA_TourActivityCancelRQ>
~~~


### CancelRQ Description




| **Element**					| **Number**	| **Type**	| **Description**			|
| --------------------------------------------- | ------------- | ------------- | ------------------------------------- |
| OTA_TourActivityCancelRQ			| 1             |		| Root node.				|
| @PrimaryLangID      				| 1      	| String	| Language code (ISO 3166-1 alpha-2) format. |
| Confirmation        				| 1             |		| Contains information of the activity booked. |
| @ID                 				| 1      	| String 	| Activity booked identifier.		|
| @type               				| 1      	| String 	| Activity booked type (Possible values: "PROVIDER"). |



### CancelRS Example



~~~xml
    <OTA_TourActivityCancelRS xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <operationImplemented>true</operationImplemented>
      <Reservation ResStatus="Cancel">
        <CancelConfirmation>
          <UniqueID ID="1283479#1" Type="PROVIDER" />
        </CancelConfirmation>
        <ReservationInfo>
          <Pricing>
            <Summary Amount="0.000" CurrencyCode="EUR" />
          </Pricing>
        </ReservationInfo>
      </Reservation>
    </OTA_TourActivityCancelRS>
~~~


### CancelRS Description




| **Element**				| **Number**	| **Type**	| **Description**				|
| ------------------------------------- | ------------- | ------------- | --------------------------------------------- |
| OTA_TourActivityCancelRS		| 1           	|		| Root node.					|
| @PrimaryLangID    			| 1    		| String	| Language code (ISO 3166-1 alpha-2) format.	|
| Confirmation      			| 1           	|		| Contains information of the activity booked.	|
| @ID               			| 1    		| String	| Activity booked identifier.			|
| @type             			| 1    		| String	| Activity booked type (Possible values: "PROVIDER").|
| Reservation       			| 1           	|		| Information about reservation status.		|
| @ResStatus        			| 1    		| Enum  	| Information about reservation status (Possibles types: "Cancel" or "Unknow"). |
| CancelConfirmation			| 1           	|		| Contains information of the activity booked.	|
| CancelConfirmation/UniqueID		| 1           	|		| Contains information of the activity booked.	|
| @ID               			| 1    		| String	| Activity booked identifier.			|
| @type             			| 1    		| String	| Activity booked type (Possible values: "PROVIDER").|
| ReservationInfo   			| 1           	|		| Information about price after cancellation call. |
| ReservationInfo/Pricing/Summary	| 0..1        	|		| Summary price for option, this element we return if OpenAvailability = false. |
| @Amount           			| 0..1 		| Decimal	| Option price. 				|
| @CurrencyCode     			| 0..1 		| String 	|Currency code (ISO 4217).			|


