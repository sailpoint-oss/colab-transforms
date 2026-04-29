## First Name Last Name Username Generator

This transform generates a lowercase firstname.lastname username format (e.g. john.smith) commonly used for Active Directory account provisioning.

### Required Attributes
- **First_Name** - The first name attribute from your HR source
- **Last_Name** - The last name attribute from your HR source

### Usage
Update the `sourceName` value to match your HR source name in ISC before applying this transform.

### Output Example
- John Smith → john.smith
- Alexander King → alexander.king
