
## LAB 3 - Try Developer Portal

Prerequisite:
- Completed Lab 1 and Lab2
  

1. Go to Developer Portal 
   ```
   https://github.com/adithaha/workshop-3scale/blob/master/finto/url.md
   ```
2. User registration
   ```
   Top right corner menu - Sign in - Sign up
     Review custom NPWP field is there
     Custom legal term also showed at the bottom
   All entries must be filled.
   ```
3. Account activation via admin
   ```
   Go to admin portal 
   Audience - Accounts - Listing - Activate
   ```
4. Go back to developer portal, login
   ```
   Top right corner menu - Sign in
   Review API documentation at DOCUMENTATION tab.
   ```
5. Register Finto API
   ```
   APPLICATIONS -> Create new applications -> select finto
   Plan: basic
   Name: finto-client
   Description: finto-client
   Create Application
   Note down your unique user key (eg. bb629d06ad6bf40c736a735a315836cba).
   ```
6. Try calling vocabularies API using your key
   ```
   Go to DOCUMENTATION tab
   GET /vocabularies
   LANG: en
   USER_KEY: #user-key
   Try it out!

   You should be able to see response.
   ```
7. Try calling types API using your key
   ```
   Go to DOCUMENTATION tab
   GET /types
   LANG: en
   USER_KEY: #user-key
   Try it out!

   You should see Authentication failed response.
   ```
8. Upgrade plan to premium
   ```
   Go to APPLICATIONS tab
   finto-client
   basic > review/changes
   Review your existing basic plan
    GET_vocabularies 60 hit / minute
   Select premium plan
    GET_vocabularies 6000 hit / minute
    GET_types 6000 hit / minute
   Request Plan Change
   ```
9. Try calling types API again using  new plan, you should be able to see response.
10. Review your usage
   ```
   Go to STATISTICS tab. You should be able to see your usage statistic.
   ```
