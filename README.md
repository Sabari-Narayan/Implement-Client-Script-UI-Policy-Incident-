# Implement Client Script & UI Policy (Incident)

## Team Details

**Team ID:** `6ab636abdcdae33acb393f Fc1`

**Project Name:** Implement Client Script & UI Policy (Incident)

### Team Leader

* **Sabari Narayanan S**

### Team Members

1. Buvanesh G
2. Vikas Samuel S
3. G Haris

---

## 📌 Problem Statement

Incident records often require consistent and accurate data entry to ensure effective triage, routing, and resolution. However, relying solely on user awareness and manual checks can lead to incomplete, inconsistent, or incorrect data being submitted.

This can impact:

* Reporting accuracy
* SLA compliance
* Incident routing
* Data consistency
* Overall service quality

To address this challenge, there is a need to enforce conditional field behavior and validation directly at the user interface level.

Implementing standardized **UI Policies** and **Client Scripts** helps control field visibility, mandatory status, and save-time validation, ensuring that Incident records meet defined business rules before they are submitted.

---

## 🎯 Objective

The objective of this project is to demonstrate how **ServiceNow client-side controls** can be used to enforce data integrity on Incident records.

The implementation demonstrates how **UI Policies** and **Client Scripts** can:

* Dynamically make fields mandatory
* Auto-populate field values
* Control field behavior
* Validate user input
* Prevent incorrect record submission
* Maintain consistent Incident data

The solution ensures that Incidents are created with complete and valid information, improving data quality and consistency across the ServiceNow platform.

---

## 🛠️ Technologies & Skills

* ServiceNow
* Incident Management
* UI Policy
* UI Policy Actions
* Client Scripts
* Form Validation
* JavaScript
* ServiceNow Incident Form

---

## ⚙️ Project Implementation

### 1. UI Policy

UI Policies are used to dynamically control fields on the Incident form based on specific conditions.

They can be used to:

* Make fields mandatory
* Make fields non-mandatory
* Make fields visible or hidden
* Enable or disable fields

---

### 2. UI Policy Actions

UI Policy Actions define how individual fields should behave when the UI Policy condition is satisfied.

In this project, UI Policy Actions are used to control fields such as:

* **Assigned To**
* **Urgency**

based on Incident conditions such as **Impact**.

---

### 3. Client Scripts

Client Scripts are used to implement client-side logic on the Incident form.

The project demonstrates different Client Script types:

#### onChange

The `onChange` Client Script executes when the value of a field changes.

It is used to dynamically update related field values based on user input.

#### onSubmit

The `onSubmit` Client Script executes when the user attempts to submit the Incident record.

It is used for form validation and can prevent submission when required conditions are not satisfied.

#### onCellEdit

The `onCellEdit` Client Script is used to control and validate changes made directly to fields in list views.

---

## 🔄 Working Flow

```text
User opens Incident Form
          ↓
User enters / modifies Incident details
          ↓
Impact value changes
          ↓
UI Policy / Client Script evaluates the condition
          ↓
Fields are dynamically updated
          ↓
Assigned To / Urgency behavior is controlled
          ↓
User submits the Incident
          ↓
onSubmit validation is executed
          ↓
Valid Data → Incident is submitted
          ↓
Invalid Data → Submission is prevented
```

---

## 📋 Key Features

| Feature                | Description                                               |
| ---------------------- | --------------------------------------------------------- |
| Dynamic Field Behavior | Fields respond automatically to Incident conditions       |
| Mandatory Fields       | Required fields can be enforced dynamically               |
| Auto-Population        | Values can be automatically populated based on conditions |
| Form Validation        | User input is validated before submission                 |
| Submission Control     | Invalid records can be prevented from being submitted     |
| Data Integrity         | Helps maintain accurate and consistent Incident records   |
| User Experience        | Reduces manual effort and improves form usability         |

---

## 📚 Learning Outcomes

Through this project, the team gained practical knowledge of:

* Creating and configuring UI Policies
* Creating UI Policy Actions
* Developing Client Scripts
* Using `onChange`, `onSubmit`, and `onCellEdit`
* Performing client-side form validation
* Dynamically controlling Incident fields
* Improving data integrity in ServiceNow
* Understanding Incident Management workflows

---

## ✅ Conclusion

The **Implement Client Script & UI Policy (Incident)** micro project effectively demonstrates how UI Policies and Client Scripts can work together to enforce dynamic field behavior, automate updates, and prevent incorrect data submission on Incident forms.

By using **onChange, onSubmit, and onCellEdit Client Scripts** alongside **UI Policy Actions**, the project ensures that fields such as **Assigned To** and **Urgency** respond appropriately to changes in **Impact**.

This solution not only enforces mandatory fields and controls user interactions but also remains lightweight, efficient, and easy to implement. It provides a practical demonstration of how client-side controls can improve **form usability, data quality, and data integrity** in ServiceNow.

---

## 👥 Team

**Team Leader:**
Sabari Narayanan S

**Team Members:**

* Buvanesh G
* Vikas Samuel S
* G Haris

---

### Project Type

**ServiceNow Micro Project**

### Domain

**IT Service Management (ITSM)**
