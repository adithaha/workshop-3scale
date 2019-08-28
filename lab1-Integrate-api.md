
## LAB 1 - Integrate API

1. Login into 3Scale admin portal
2. New
	- Name: JBossFuse
	- Type: Linux
	- Version: Fedora (64-bit)	
3. Memory 3096MB
4. Use an existing virtual hard disk file JBossFuse.vdi
5. Create


###  environment - with VMPreparing

ssh into the machine, user user/pass below: jboss/jboss
```
#start postgresql
$ sudo su
<password>
$ docker start postgres94
```


### Preparing environment - with OpenShift

Login into OpenShift
```
Create Project
	Name: fuse-<name>
	Create
Add to Project - Browse Catalog - Databases - Postgres - PostgreSQL (Ephemeral) - Next
	PostgreSQL Connection Username: postgres
	PostgreSQL Connection Password: postgres
	PostgreSQL Database Name: dsEmployee
	Create
```

### Import database table


Open postgreql-ephemeral pod - Terminal
```
$ createdb dsEmployee
$ vi ddl.sql

copy ddl.sql content here

$ psql -h localhost postgres -f ddl.sql postgres
```
