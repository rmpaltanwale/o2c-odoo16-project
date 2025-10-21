# Order 2 Cash - Odoo 16

<!-- It's common to insert a short (1-2 sentence) summary of the project here -->

## 📚 Table of Contents

- [Background Business Case](#background-business-case)
- [Goals](#goals)
- [Implementation](#implementation)
- [Process](#process)
  - [Customer](#1️⃣-customer)
  - [Products](#2️⃣-products)
  - [Quotation & Sales Orders](#3️⃣-quotation--sales-orders)
  - [Processing & Delivery](#4️⃣-processing--delivery)
  - [Invoicing & Payment collection](#5️⃣-invoicing-&-payment-collection)

## Background Business Case

This is a supply chain business case for the hypothetical company Banana Inc., a grocery store. From start to finish, this document describes how customer order processing, invoicing, order validation, delivery and payment collection is implemented in Odoo 16’s Order to Cash workflow.

## Goals

The goal of this project is to establish a new workflow for processing, invoicing, order validating, delivering and collecting payment for the business to function more smoothly. Prior to this, the company was using an outdated system. This implementation will add value by increasing order processing speed, organization, and better allocation of company resources.

## Implementation

The implementation will be carried out with an Order 2 Cash process. The order to cash (O2C) process is the entire business workflow from the moment a customer places an order to when the company receives and records the final payment. The following modules/apps are used:

![Modules](./Screenshots/Modules.png "Modules")

## Process

### 1️⃣ Customer

Contacts (module) → Create the customer

My first step was to create customer records - the foundation of the O2C cycle. In Odoo, every sales transaction must be linked to a Contact, representing either an individual or a business entity.

#### Individual Customer Example Form

![Individual Customer Form](./Screenshots/Individual_customer.png "Individual Customer Form")

#### Business Customer Example Form

![Business Customer Form](./Screenshots/Business_customer.png "Business Customer Form")

For this business case, I created 10 individual customers and 10 business customers:

![Customer List](./Screenshots/Customer_list.png "Customer List")

Each customer profile included details such as:

- Name

- Street / City / State / ZIP

- Email / Phone

- Payment Terms

I treated this as the foundation of the O2C workflow - accurate customer data ensures proper invoicing, reporting, and follow-up communication. I wanted to capture the diversity of a mixed clientele, so both individuals and companies were included.

### 2️⃣ Products

Inventory (module) → Products (drop down list) → Products (option) → New

Once customers were in place, my next goal was to define what Banana Inc. sells. The Products section in Odoo allows configuration of items that can be sold, purchased, or stored in inventory.

Each product record included:

- Product Name and Internal Reference (e.g., BW001 for Bottled Water)

- Product Type (Storable)

- Sales Price and Cost

- Quantity on Hand / Forecasted Quantity

- Unit of Measure (e.g., Unit, Dozen)

- Image for visual distinction

Categories created:

1. Food Items - Burgers, Nuggets, Muffins

2. Beverages - Bottled Water, Soft Drinks

3. Cleaning & Hygiene Supplies - Gloves, Sanitizers, Sprays

4. Packaging & Disposable Items - Takeaway Bags, Paper Straws

Here is an example of the form of a water bottle:

![water bottle](./Screenshots/Bottled_Water.png "Bottled Water").

I created in total 20 different products, each with a distinct image to distinguish it from the other. 

![20 different products](./Screenshots/Products_list.png "Products List")

These products range from Food Items, Beverages, Cleaning & Hygiene Supplies, to Packaging & Disposable Items.

![distinct image to distinguish it from the other](./Screenshots/Products_list_images.png "Products List Images")

I designed these categories to simulate inventory management complexity. The use of internal references and categories helps future automation, such as reordering and reporting. Including images added realism and professional presentation. 

### 3️⃣ Quotation & Sales Orders

This stage connected customers and products into real transactions.

For each sale, I:

Created a Quotation. Here’s an example of a quotation’s form:

![quotation form](./Screenshots/Quotation_form.png "Quotation Form")

After confirming, I reviewed each sales order to ensure all ordered quantities and prices
matched expectations.

The next step is to click on the “confirm” button on the top left; this converts the quotation into a sales order.

![converts the quotation into a sales order](./Screenshots/Sales_order_form.png)

Then, update the quantities in sales order.

![quantities in sales order](./Screenshots/SO_form_quantity_updated.png)

This was the stage where Odoo transitioned from planning to commitment — quotations represent proposals, and sales orders formalize them. I ensured every quotation matched real customer types to make the O2C cycle realistic.

### 4️⃣ Processing & Delivery

The sales orders having been created, the next step is to validate them. Click on the delivery button with the truck symbol on it.

Once a Sales Order was confirmed, Odoo automatically generated a Delivery Order.
Here’s how I processed each one:

Opened the Delivery Order by clicking the truck icon on the Sales Order.

![delivery button](./Screenshots/Delivery_symbol.png)

This opens the delivery order form.

![delivery order form](./Screenshots/Delivery_order_form.png)

Update the quantities in the “Done” column to match the corresponding quantities in the “Demand” column.

![Update the quantities](./Screenshots/Delivery_quantity.png)

Now, click validate (top left). This completes the delivery process.

![Click validate (top left)](./Screenshots/Delivery_validate.png)

I paid close attention to inventory synchronization here. My goal was to ensure that deliveries only occurred for available stock. This step illustrated how Odoo ensures supply chain accuracy by automatically adjusting stock levels post-delivery.

### 5️⃣ Invoicing & Payment Collection

Now, the final step. The delivery of the goods to the customer is not enough; the payment must be collected to complete the O2C process. 
To do this, open the Sales module, and click on the To Invoice option on the purple ribbon.

![To invoice](./Screenshots/To_invoice.png)

Clicking on To Invoice will open a dropdown list with the following 2 options: Orders to Invoice and Orders to Upsell. Click on Orders to Invoice. This shows the Sales Order we delivered earlier. Click on it.

![Dropdown list](./Screenshots/Dropdown_list_invoice.png)

The invoice form opens. Here, click on Create invoice (top left).

![Invoice form](./Screenshots/Invoice_form.png)

A prompt dialog box opens. Keep regular invoice option selected and then proceed with “Create and View Invoice”.

![Create and View Invoice](./Screenshots/Create_invoice_dialog_box.png)

Draft invoice is created. To proceed, click confirm.

![Confirm draft invoice](./Screenshots/Confirm_draft_invoice.png)

Customer invoice has been posted. Click on Register Payment.

![Payment register](./Screenshots/Register_payment_for_posted_invoice.png)

Dialog box opens again. Click on Create Payment.

![Payment create](./Screenshots/Create_payment.png)

Payment has been processed and completed.

![Payment processed](./Screenshots/Customer_invoice_paid.png)

This stage tied everything together — the transaction was now complete financially and operationally. Registering payments gave me firsthand insight into how Odoo updates accounting entries, customer ledgers, and order statuses in real-time.
