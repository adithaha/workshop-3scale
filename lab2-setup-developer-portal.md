
## LAB 2 - Setup Developer Portal

Prerequisite:
- Completed Lab 1
  
1. Login into 3Scale admin portal - Tab Audience - Developer Portal - Content
2. Change homepage title to Finto API - Homepage
   ```
   line 5: <h1>Echo API</h1>
   change to <h1>Finto API</h1>
   Save
   ```
3. Change Documentation description to Finto API - Documentation
   ```
   line 5: <p>Use our live documentation to learn about the Echo API</p>
   change to <p>Use our live documentation to learn about the Finto API</p>
   Save
   ```
4. Add new field. Top Left Tab - Accounts - Field Definitionn
   ```
   Account - Create
   Name: npwp
   label: NPWP
   Required: checked
   Create
   ```
5. Add legal term. Developer Portal - Legal Term - Signup
   ```
   Subject to the terms and conditions of this Agreement and the License Agreement, you hereby grants to Red Hat, and Red Hat hereby accepts, a non-exclusive, non-transferable, non-sublicenseable, limited license to install and execute the object code version of the Software solely for the limited purpose to receive, store, display and exhibit the Digital Content Service, the Traditional Content Program and the Digital Carousel, as applicable, on the LLC Equipment solely in connection with its performance of and subject to all of the terms and conditions of this Agreement and only to the extent such Software is utilized by Red Hat.
   ```
   Update
6. Open your Portal to the world
   ```
   Developer Portal - Content
   Open your Portal to the world
   ```
