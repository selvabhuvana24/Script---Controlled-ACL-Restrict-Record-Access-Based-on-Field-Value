# Script – Controlled ACL: Restrict Record Access Based on Field Value

## Project Overview

This project demonstrates how to implement a script-controlled Access Control List (ACL) in ServiceNow to restrict users from accessing records based on specific field values.

In this scenario, only users belonging to the EEE branch are allowed to view records where the Branch field is set to EEE, while administrators retain full access.

The project also implements READ, CREATE, WRITE, and DELETE access controls using custom user roles to ensure secure record management.

## Objectives

* Implement script-controlled ACLs in ServiceNow.
* Restrict record visibility based on field values.
* Create and manage users and custom roles.
* Control READ, CREATE, WRITE, and DELETE operations.
* Prevent unauthorized access to sensitive information.
* Provide administrators with full access to records.

## Technologies Used

* ServiceNow Platform
* Access Control Lists (ACL)
* JavaScript
* ServiceNow Scripting
* User and Role Management

## Project Modules

### 1. Creation of Users and Roles

* Created a test user named EEE User.
* Created custom roles: bb1, bb2, bb3, and bb4.
* Assigned the roles to the EEE user.

### 2. Table Creation

Created a custom table named **Institution Details** (`u_institution_details`) with the following fields:

| Field               | Type                   |
| ------------------- | ---------------------- |
| Student Roll Number | Auto Number            |
| Student Name        | Reference – User       |
| Faculty Name        | Reference – User       |
| Branch              | Choice (ECE, EEE, CSE) |
| Email               | String                 |
| Phone Number        | String                 |
| Description         | Multi String           |

### 3. READ ACL

* Requires the custom role bb1.
* Includes a data condition for Branch = EEE.
* Allows administrators to view all records.
* Allows authorized EEE users to view EEE records.
* Restricts users without the required role.

### 4. CREATE ACL

* Requires the custom role bb2.
* Controls the creation of new records.
* Allows users with the required permissions to access the New button.

### 5. WRITE ACL

* Requires the custom role bb3.
* Controls modification of existing records.
* Prevents unauthorized users from editing records.

### 6. DELETE ACL

* Requires the custom role bb4.
* Controls deletion of records.
* Restricts unauthorized users from deleting records.

## Access Control Summary

| ACL Operation | Required Role | Purpose                    |
| ------------- | ------------- | -------------------------- |
| READ          | bb1           | View authorized records    |
| CREATE        | bb2           | Create new records         |
| WRITE         | bb3           | Modify existing records    |
| DELETE        | bb4           | Delete records             |
| Admin Access  | admin         | Full access to all records |

## How It Works

1. The administrator creates users and assigns custom roles.
2. A custom Institution Details table is created.
3. Student records are added with different branch values.
4. ACL rules are configured for READ, CREATE, WRITE, and DELETE operations.
5. The system evaluates user roles and field conditions.
6. Authorized users are granted access to permitted operations.
7. Unauthorized users are restricted from accessing protected records.

## Testing and Results

The project was tested by impersonating different users in ServiceNow.

* **EEE User:** Can view only EEE branch records when the required READ role is assigned.
* **User without the required role:** Cannot view restricted records.
* **Administrator:** Can view all records regardless of branch.
* **Authorized users:** Can perform CREATE, WRITE, and DELETE operations according to their assigned roles.


## Conclusion

The Script-Controlled ACL project demonstrates how ServiceNow can enforce record-level security using user roles, field conditions, and scripts.

By implementing READ, CREATE, WRITE, and DELETE ACLs, the project provides controlled access to records, protects sensitive information, and ensures that users can perform only the operations permitted by their assigned roles.

---

**Developed as part of the Naan Mudhalvan Programme.**
