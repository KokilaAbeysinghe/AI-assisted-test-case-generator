# Hardware Shop POS System
## User Management — Software Requirements Specification

### 1. Feature Overview

The User Management module allows authorized administrators to create, view, update, deactivate, and manage system users and their roles within the Hardware Shop POS system.

The purpose of this module is to ensure that users have appropriate access to system functions based on their assigned roles.

---

## 2. User Roles

The system shall support the following user roles:

| Role | Description |
|---|---|
| Administrator | Has full access to User Management and system functions |
| Manager | Can manage operational functions but cannot manage administrators |
| Cashier | Can perform sales and payment-related activities |
| Inventory Officer | Can manage products and inventory |

---

## 3. Functional Requirements

### User Registration / Creation

**REQ-USER-001**  
The Administrator shall be able to create a new system user.

**REQ-USER-002**  
The system shall require the Administrator to enter the following information when creating a user:
- Full Name
- Username
- Email Address
- Password
- Confirm Password
- Role

**REQ-USER-003**  
The system shall prevent creation of a user when any mandatory field is empty.

**REQ-USER-004**  
The system shall verify that the username is unique before creating a new user.

**REQ-USER-005**  
The system shall verify that the email address is not already associated with another user.

**REQ-USER-006**  
The system shall verify that Password and Confirm Password contain the same value.

**REQ-USER-007**  
The system shall allow the Administrator to select a role for the new user.

**REQ-USER-008**  
The system shall create the user account when all required information is valid.

**REQ-USER-009**  
The system shall display a confirmation message after successfully creating a user.

---

### View Users

**REQ-USER-010**  
The Administrator shall be able to view a list of registered users.

**REQ-USER-011**  
The user list shall display, at minimum:
- Full Name
- Username
- Email Address
- Role
- Account Status

**REQ-USER-012**  
The Administrator shall be able to search for a user using the username or full name.

**REQ-USER-013**  
The system shall display an appropriate message when no users match the search criteria.

---

### Update User

**REQ-USER-014**  
The Administrator shall be able to update the information of an existing user.

**REQ-USER-015**  
The Administrator shall be able to change a user's:
- Full Name
- Email Address
- Role

**REQ-USER-016**  
The system shall validate updated user information before saving changes.

**REQ-USER-017**  
The system shall display a confirmation message after successfully updating a user.

---

### User Activation and Deactivation

**REQ-USER-018**  
The Administrator shall be able to deactivate an active user account.

**REQ-USER-019**  
The Administrator shall be able to activate a previously deactivated user account.

**REQ-USER-020**  
The system shall display the current account status of each user.

**REQ-USER-021**  
A deactivated user shall not be allowed to log into the system.

**REQ-USER-022**  
The system shall display an appropriate message when a deactivated user attempts to log in.

---

### Password Management

**REQ-USER-023**  
The system shall mask the password when it is entered.

**REQ-USER-024**  
The user shall be able to change their password after logging into the system.

**REQ-USER-025**  
The system shall require the user to enter their current password before changing it.

**REQ-USER-026**  
The system shall require the new password and confirmation password to match.

**REQ-USER-027**  
The system shall display an appropriate validation message when the password change fails.

---

### Role-Based Access Control

**REQ-USER-028**  
The system shall restrict access to system functions based on the user's assigned role.

**REQ-USER-029**  
Only Administrators shall be able to access the User Management module.

**REQ-USER-030**  
A Cashier shall not be able to access Administrator-only functions.

**REQ-USER-031**  
An Inventory Officer shall be able to access inventory-related functions according to their assigned permissions.

**REQ-USER-032**  
A Manager shall be able to access management functions according to their assigned permissions.

**REQ-USER-033**  
The system shall prevent unauthorized users from accessing restricted functions by directly entering a restricted URL.

---

### User Deletion

**REQ-USER-034**  
The Administrator shall be able to delete a user account if the system permits permanent deletion.

**REQ-USER-035**  
The system shall request confirmation before permanently deleting a user.

**REQ-USER-036**  
The system shall display a confirmation message after successfully deleting a user.

---

## 4. Validation Requirements

**REQ-USER-037**  
The system shall validate the email address format before saving a user.

**REQ-USER-038**  
The system shall reject an email address with an invalid format.

**REQ-USER-039**  
The username shall not contain unsupported characters.

**REQ-USER-040**  
The system shall prevent duplicate usernames.

**REQ-USER-041**  
The system shall prevent duplicate email addresses.

**REQ-USER-042**  
The system shall display clear validation messages when user input is invalid.

---

## 5. Security Requirements

**REQ-USER-043**  
Passwords shall not be displayed in plain text in the user interface.

**REQ-USER-044**  
The system shall not allow unauthorized users to access user-management functions.

**REQ-USER-045**  
The system shall prevent a user from accessing functions that are not permitted for their assigned role.

**REQ-USER-046**  
The system shall protect user credentials from being exposed through the user interface.

---

## 6. Audit Requirements

**REQ-USER-047**  
The system shall record important user-management activities performed by Administrators.

The activities should include, where applicable:
- User creation
- User information update
- User activation
- User deactivation
- User deletion
- Role changes

**REQ-USER-048**  
The system shall record the date and time of important user-management activities.

**REQ-USER-049**  
The system shall record the user who performed the administrative action.

---

## 7. Assumptions Requiring Business Clarification

The following items have intentionally **not** been given specific values because they should normally be confirmed with the Business Analyst/Product Owner:

1. What is the minimum password length?
2. What characters are required in a password?
3. What is the maximum username length?
4. What characters are allowed in usernames?
5. Should usernames be case-sensitive?
6. Should email addresses be case-sensitive?
7. How many failed login attempts should cause an account lock?
8. How long should an account remain locked?
9. Should Administrators be allowed to delete their own account?
10. Should the last remaining Administrator be prevented from being deleted?
11. Should deleted users be permanently removed or only deactivated?
12. Which exact functions should be available to Managers, Cashiers, and Inventory Officers?
13. Should user-management activities be available in an audit-log screen?