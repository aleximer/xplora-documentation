**1: Custom Login Page without Bank ID**

As a user, I want to access a custom login page that doesn't require Bank ID authentication,
So that I can log in using alternative methods.
Acceptance Criteria:
A separate login page is accessible without the need for Bank ID.

**Estimation: 2-3h**


**2: Login with Phone Number Verification**

As a user, I want to log in by entering my phone number and verifying it through an SMS code,
So that my identity can be verified securely without Bank ID.
Acceptance Criteria:
The user is prompted to enter their phone number upon login.
An SMS with a verification code is sent to the provided phone number.
The user must enter the received code to proceed with the login.

**Estimation: 5-6h**

**3: Form Filling with Pre-filled Phone Number**

As a user, I want to fill out a form with various fields, where my phone number is pre-filled and locked based on my previous verification,
So that I can provide additional information securely and efficiently.
Acceptance Criteria:
A form is presented to the user with various fields to be filled out.
The phone number field is pre-filled and **locked** based on the phone number provided in the previous step.

**Estimation: 2-3h**

**4: User Story: Email Notification with Submitted Information**

As an administrator, I want to receive an email with the user's submitted information and their IP address,
So that I can have a record of the submission for further processing or verification.
Acceptance Criteria:
An email is sent to the administrators containing the information filled out by the user in the form.
The email includes the user's IP address.

**Estimation: 2-3h**

| Name | Low | High |
| ---- | ---- | ---- |
| `Custom Login Page without Bank ID` | `2` | `3` |
| `Login with Phone Number Verification` | `5` | `6` |
| `Form Filling with Pre-filled Phone Number` | `3` | `4` |
| `Email Notification with Submitted Information` | `2` | `3` |
|  | `12` | `16` |
