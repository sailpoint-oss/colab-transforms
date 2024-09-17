The Local Time Lookup Offset Transform looks at a user’s Country and Location attributes in the "External Users" Source and uses these values to perform date maths on the date and time now. The date maths do two things:

First:, they add 7 hours for every country or location, this is to ensure the account disabled 7 hours early (5PM on the users end date, rather than midnight).

Second: It adds or removes hours based on the users Timezone, determined by a user’s Country and Location attributes in the "External Users" Source
