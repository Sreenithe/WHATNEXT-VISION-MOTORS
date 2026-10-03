# WHATNEXT-VISION-MOTORS
🚗 Salesforce CRM solution for WhatNext Vision Motors with automated vehicle ordering, stock validation, dealer assignment, test-drive reminders, and Apex-based order processing.

WhatNext Vision Motors 🚗

Shaping the Future of Mobility with Innovation and Excellence

WhatNext Vision Motors is a Salesforce CRM project designed to
improve customer experience and streamline vehicle ordering and
operational processes in an automotive business.

The system manages vehicles, dealers, customers, vehicle orders, test
drives, and service requests while using Salesforce automation, Flow,
Apex Triggers, Batch Apex, and Scheduled Apex to reduce manual work and
enforce business rules.

📌 Project Overview

The project focuses on building an efficient vehicle management and
ordering system in Salesforce.

The main objectives are to:

Automatically assign orders to the nearest dealer based on customer
location.

Prevent customers from ordering vehicles that are out of stock.

Track vehicle stock and order status.

Automatically update pending orders when stock becomes available.

Send automated email reminders for scheduled test drives.

Manage customer, dealer, vehicle, order, test drive, and service
information.

Reduce administrative work through Salesforce automation.

✨ Key Features

1. Vehicle Management

Store vehicle details.

Maintain vehicle model, price, stock quantity, dealer, and
availability status.

Track available, out-of-stock, and discontinued vehicles.

2. Customer Management

Store customer name, email, phone number, address, and preferred
vehicle type.

Link customers with their vehicle orders and test drives.

3. Dealer Management

Store dealer information and location.

Associate vehicles and orders with dealers.

4. Smart Dealer Assignment

A Record-Triggered Flow retrieves customer information and identifies
the dealer based on the customer's location before assigning the
relevant dealer to the order.

5. Stock Validation

Apex Trigger and Trigger Handler logic checks vehicle stock before an
order can be placed.

If the vehicle has no available stock, the order is prevented with an
error message.

6. Automatic Stock Update

When a confirmed order is placed, the corresponding vehicle stock
quantity is reduced automatically.

7. Test Drive Reminder

A Record-Triggered Flow schedules an email reminder one day before a
customer's scheduled test drive.

8. Pending Order Processing

A Batch Apex process checks pending orders and confirms them when stock
becomes available.

9. Scheduled Batch Processing

A Scheduled Apex class is used to execute the vehicle order batch
process automatically.

🏗️ Salesforce Architecture

The project uses the following Salesforce components:

Salesforce CRM

Custom Objects

Custom Fields

Custom Tabs

Lightning App Builder

Record-Triggered Flows

Apex Trigger

Apex Trigger Handler

Batch Apex

Scheduled Apex

🗃️ Data Model

The project defines the following main custom objects:

Object                         Purpose

Vehicle__c                   Stores vehicle details and stock information
Vehicle_Dealer__c            Stores authorized dealer information
Vehicle_Customer__c          Stores customer details
Vehicle_Order__c             Tracks vehicle purchases
Vehicle_Test_Drive__c        Tracks test drive bookings
Vehicle_Service_Request__c   Tracks vehicle servicing requests

Main Relationships

Vehicle Customer
      │
      ├──────────────► Vehicle Order ◄────────────── Vehicle
      │
      ├──────────────► Test Drive ◄─────────────────┘
      │
      └──────────────► Service Request ◄────────────┘

Vehicle
   │
   └──────────────► Dealer

📋 Important Fields

Vehicle__c

Vehicle_Name__c

Vehicle_Model__c

Stock_Quantity__c

Price__c

Dealer__c

Status__c

Vehicle status values include:

Available

Out of Stock

Discontinued

Vehicle_Dealer__c

Dealer_Name__c

Dealer_Location__c

Dealer_Code__c

Phone__c

Email__c

Vehicle_Order__c

Customer__c

Vehicle__c

Order_Date__c

Status__c

Order status values include:

Pending

Confirmed

Delivered

Canceled

Vehicle_Customer__c

Customer_Name__c

Email__c

Phone__c

Address__c

Preferred_Vehicle_Type__c

Vehicle_Test_Drive__c

Customer__c

Vehicle__c

Test_Drive_Date__c

Status__c

Test drive status values include:

Scheduled

Completed

Canceled

Vehicle_Service_Request__c

Customer__c

Vehicle__c

Service_Date__c

Issue_Description__c

Status__c

Service request status values include:

Requested

In Progress

Completed

⚙️ Automation Workflow

Vehicle Order Flow

Customer Creates Vehicle Order
            │
            ▼
     Check Order Status
            │
            ▼
     Get Customer Details
            │
            ▼
     Identify Dealer by Location
            │
            ▼
      Assign Dealer to Order

Stock Validation Flow

Vehicle Order Created/Updated
            │
            ▼
       Apex Trigger
            │
            ▼
      Check Vehicle Stock
        /             \
       /               \
Stock Available     Out of Stock
      │                  │
      ▼                  ▼
Continue Order       Prevent Order

Pending Order Processing

Pending Order
     │
     ▼
Batch Apex Runs
     │
     ▼
Check Vehicle Stock
     │
 ┌───┴───────────────┐
 │                   │
Stock Available   Still Out of Stock
 │                   │
 ▼                   ▼
Confirmed          Remains Pending
 │
 ▼
Decrease Stock

Test Drive Reminder

Test Drive Status = Scheduled
              │
              ▼
      Scheduled Path
              │
              ▼
      1 Day Before Test Drive
              │
              ▼
       Send Email Reminder

💻 Apex Components

Trigger Handler

The project uses a trigger handler named:

VehicleOrderTriggerHandler

The handler contains logic for:

Preventing orders when vehicle stock is unavailable.

Updating vehicle stock after confirmed orders.

Vehicle Order Trigger

The trigger operates on:

before insert

before update

after insert

after update

It delegates processing to the trigger handler.

Batch Apex

VehicleOrderBatch processes pending vehicle orders.

Its documented purpose is to:

Retrieve pending orders.

Check the stock of the associated vehicles.

Confirm orders when stock becomes available.

Reduce the corresponding stock quantity.

Scheduled Apex

VehicleOrderBatchScheduler executes the batch job through Salesforce
scheduling.

🛠️ Technology Stack

Technology                      Usage

Salesforce CRM              Main CRM and application platform
Salesforce Custom Objects   Data management
Lightning App Builder       Application interface
Salesforce Flow             Process automation
Apex                        Business logic
Apex Triggers               Event-driven automation
Batch Apex                  Bulk order processing
Scheduled Apex              Automated batch execution

🚀 Salesforce Setup

To work with the project, create a Salesforce Developer account/org and
configure the required custom objects, fields, tabs, and automation.

The project document specifies creating a Salesforce Developer account
through the Salesforce Developer signup page:

https://developer.salesforce.com/signup

After creating the org, configure:

Custom Objects

Custom Fields

Object Relationships

Custom Tabs

Lightning App

Record-Triggered Flows

Apex Trigger Handler

Apex Trigger

Batch Apex

Scheduled Apex

📂 Suggested GitHub Repository Structure

WhatNext-Vision-Motors/
│
├── README.md
│
├── force-app/
│   └── main/
│       └── default/
│           ├── classes/
│           ├── triggers/
│           ├── flows/
│           ├── objects/
│           └── tabs/
│
└── docs/
    └── project-documentation.pdf

The exact Salesforce metadata folder structure depends on how the
project is retrieved or deployed from the Salesforce org.

🎯 Project Outcomes

The project is designed to improve:

Customer ordering convenience

Order accuracy

Vehicle stock management

Dealer assignment

Test drive communication

Order fulfillment tracking

Operational efficiency

Reduction of repetitive administrative work

📚 Learning Areas

This project provides practical exposure to:

Salesforce CRM

Data Modelling

Fields and Relationships

Lightning App Builder

Record-Triggered Flows

Apex Programming

Apex Triggers

Trigger Handler Pattern

Batch Apex

Scheduled Apex

Salesforce Automation

Custom Objects and Tabs

👥 Team

Team ID: 6ab3a129d7422676bb28aa1d

Team Member

Hari S
Hariharan G
Sreenithe V
Ravichandran A
Rohan M

Institution: Anjalai Ammal-Mahalingam Engineering College
Demo Link: https://drive.google.com/file/d/1M9ESoERu6z6J7Px0gzlrbeWkvFI7Ixgy/view?usp=drive_link
