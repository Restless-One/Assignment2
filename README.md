# README.md

git repository link: https://github.com/Restless-One/A2-YiHao-20304156?tab=readme-ov-file

### Task 1
 Done at 6 OCT
![image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/Screenshot%202024-10-06%20at%204.25.42%E2%80%AFpm.png)

### Task 2
 Done at 7 OCT
#### Show Contact
 ![image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/show%20contact.png)

#### Add Contact
 ![image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/add%20contect%20command.png)

#### Delete Contact
 ![image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/Delete%20contact%20command.png)

#### Update Contact
 ![image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/update%20contact.png)

#### Show Phone
 ![image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/show%20phones.png)

#### Add Phone
 ![image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/add%20phone.png)

#### Delete Phone
 ![image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/delete%20phone.png)

#### Update Phone
 ![image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/update%20phone.png)

### Task 3
##### update contact.model
```
     const Contact = sequelize.define("contact", {
        id: {
            type: Sequelize.INTEGER,
            autoIncrement: true,
            primaryKey: true,
        },
        name: {
            type: Sequelize.STRING
        },
        address: {
            type: Sequelize.STRING,
            allowNull: true
        }
 ```
 ##### update contact.controller
 ```
     const contact = {
        name: req.body.name,
        address : req.body.address
    };
 ```
 ##### update phone.model
 ```
        phone_type: {
            type: Sequelize.STRING
        },
        phone_number: {
            type: Sequelize.STRING
        },
 ```
 ##### update phone.controller
 ```
     const phone = {
       phone_type : req.body.type,
       phone_number : req.body.number,
        contactId: parseInt(req.params.contactId)
    };
 ```
 ##### frontend adjust
 [image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/task3-front.png)

 ##### api test for task3
 
 ###### get contact
 [image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/task3-getcontact.png)
 
 ###### add contact
 [image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/task3-addcontact.png)

 ###### delete contact
 [iamge](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/task3-deletecontact.png)

 ###### update contact
 [iamge](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/task3-updatecontact.png)

 ###### get phone
 [image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/task3-getphone.png)
 
 ###### add phone
 [image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/task3-addphone.png)

 ###### delete phone
 [image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/task3-deletephone.png)

 ###### update phone
 [image](https://github.com/Restless-One/A2-YiHao-20304156/blob/main/screenshot/task3-updatephone.png)
 ### Task 4
 ####  create new table "Company"
 create a new file `company.model.js`
 code for `company.model.js`
 ```JavaScript
 module.exports = (sequelize, Sequelize) => {
    const Company = sequelize.define("company", {
        company_id: {
            type: Sequelize.INTEGER,
            autoIncrement: true,
            primaryKey: true,
        },
        company_name: {
            type: Sequelize.STRING
        },
        company_address: {
            type: Sequelize.STRING,
            allowNull: true
        },
        contactId: {
            type: Sequelize.INTEGER,
            references: {
                model: 'contacts',
                key: 'id',
            }
        }
    });

    return Company;
};
 ```
 #### API creation and test
 ###### API create:
    router.post("/contacts/:contactId/companies", companies.create);

    router.get("/contacts/:contactId/companies", companies.findAll);

    router.get("/contacts/:contactId/companies/:companyId", companies.findOne);

    router.put("/contacts/:contactId/companies/:companyId", companies.update);

    router.delete("/contacts/:contactId/companies/:companyId", companies.delete);

 ###### API test
 add company

 get company

 update company

 delete company
 



------------------------------------------------
IMPORTANT: Once you've cloned this to your forked repository, ensure that you continuously update this document as you complete each task to demonstrate your ongoing progress.

Please include your shared repository link here:

Example:
Choiru's shared repository: https://github.com/choiruzain-latrobe/Assignment2.git


Make sure for **your case it is in Private**
## Access Database
1 **Plsql Cheat Sheet:**
You can refer to the PostgreSQL cheat sheet [here](https://www.postgresqltutorial.com/postgresql-cheat-sheet/).

2 **Know the Container ID:**
To find out the container ID, execute the following command:
   ```bash
   docker ps
    9958a3a534c9   testsystem-nginx           "/docker-entrypoint.…"   6 minutes ago   Up 6 minutes   0.0.0.0:80->80/tcp   testsystem-nginx-1
    53121618baa4   testsystem-frontend        "docker-entrypoint.s…"   6 minutes ago   Up 6 minutes   3000/tcp             testsystem-frontend-1
    c89e46ac94b0   testsystem-api             "docker-entrypoint.s…"   6 minutes ago   Up 6 minutes   5000/tcp             testsystem-api-1
    9f4aea7cf538   postgres:15.3-alpine3.18   "docker-entrypoint.s…"   6 minutes ago   Up 6 minutes   5432/tcp             testsystem-db-1
   ```
3. Running the application

**docker compose command:**
   ```bash
   docker compose up --build
   ```

4 **Access postgreSQL in the container:**
Once you have the container ID, you can execute the container using the following command:
You will see the example of running the PostgreSQL inside the container.
   ```bash
   docker exec -it testsystem-db-1 psql -U postgres
   choiruzain@MacMarichoy TestSystem % docker exec -it testsystem-db-1 psql -U postgres                                       
   psql (15.3)
   Type "help" for help.
   
   postgres=# \dt
             List of relations
    Schema |   Name   | Type  |  Owner   
   --------+----------+-------+----------
    public | contacts | table | postgres
    public | phones   | table | postgres
   (2 rows)
  
    postgres=# select * from contacts;
    id |  name  |         createdAt         |         updatedAt         
   ----+--------+---------------------------+---------------------------
     1 | Helmut | 2024-08-08 11:57:57.88+00 | 2024-08-08 11:57:57.88+00
    (1 row)
    postgres=# select * from phones;
    id | phone_type |   number    | contactId |         createdAt          |         updatedAt          
   ----+------------+-------------+-----------+----------------------------+----------------------------
     1 | Work       | 081431      |         1 | 2024-08-08 11:59:04.386+00 | 2024-08-08 11:59:04.386+00


postgres=# select * from contacts;
   ```
Replace `container_ID` with the actual ID of the container you want to execute.

## Executing API

### Contact API


1. Add contacts API  (POST)
```bash
http post http://localhost/api/contacts name="Choiru"
        
choiruzain@MacMarichoy-7 TestSystem % http post http://localhost/api/contacts name="Choiru"
HTTP/1.1 200 OK
Access-Control-Allow-Origin: http://localhost:3000
Connection: keep-alive
Content-Length: 102
Content-Type: application/json; charset=utf-8
Date: Thu, 08 Aug 2024 21:01:53 GMT
ETag: W/"66-FmPYAaIkyQoroDwP2JsAZjWTAxs"
Server: nginx/1.25.1
Vary: Origin
X-Powered-By: Express

{
"createdAt": "2024-08-08T21:01:53.017Z",
"id": 1,
"name": "Choiru",
"updatedAt": "2024-08-08T21:01:53.017Z"
}

```
2 Get contacts API  (GET)

```bash
http get http://localhost/api/contacts


choiruzain@MacMarichoy-7 TestSystem % http get http://localhost/api/contacts
HTTP/1.1 200 OK
Access-Control-Allow-Origin: http://localhost:3000
Connection: keep-alive
Content-Length: 104
Content-Type: application/json; charset=utf-8
Date: Thu, 08 Aug 2024 21:04:58 GMT
ETag: W/"68-V+4KuL2xahYt8YAkKG6rKdR7wHg"
Server: nginx/1.25.1
Vary: Origin
X-Powered-By: Express

[
{
"createdAt": "2024-08-08T21:01:53.017Z",
"id": 1,
"name": "Choiru",
"updatedAt": "2024-08-08T21:01:53.017Z"
}
]


```
3. Show/create the API commmand to delete the contacts (DELETE)

```bash





```

4. Show/create the API command to edit the contacts (PUT)
```
http get http://localhost/api/contacts/1/phones

```

### Phone API
