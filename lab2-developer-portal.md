
## LAB 2 - Prepare Developer Portal

Prerequisite:
- Completed Lab 1
  

2. Delete default docs
   ```
   Active Docs - Echo - Delete - OK
   ```
2. Upload Finto docs
   ```
   Active Docs - Create your first spec
   Name: Finto
   System Name: finto
   Check Publish?
   Fill API JSON Spec from xxx
   Change line 11: "host": "finto-2445581864856.production.gw.apicast.io"
   To: "host": "api-<user>-apicast-production.anugraha-3scale.apps.rhpds3x.openshift.opentlc.com"
   Create Service
   ```
2. Promote to Production
   ```
   Integration - Configuration
   Promote v.1 to Production
   ```
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
4. Add legal term. Accounts - Field Definitionn
   ```
   Account - Create
   Name: npwp
   label: NPWP
   Required: checked
   Create
   ```
   Update
5. Add new field. Developer Portal - Legal Term - Signup
   ```
   Subject to the terms and conditions of this Agreement and the License Agreement, you hereby grants to Red Hat, and Red Hat hereby accepts, a non-exclusive, non-transferable, non-sublicenseable, limited license to install and execute the object code version of the Software solely for the limited purpose to receive, store, display and exhibit the Digital Content Service, the Traditional Content Program and the Digital Carousel, as applicable, on the LLC Equipment solely in connection with its performance of and subject to all of the terms and conditions of this Agreement and only to the extent such Software is utilized by Red Hat.
   ```
   Update
6. Open your Portal to the world
   ```
   Developer Portal - Content
   Open your Portal to the world
   ```
