# Fetching Data From SQL

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Introduction</mark>&#x20;

_**The internet is a global network of interconnected computers and servers that communicate with each other using a common set of protocols. It allows users to share information, communicate with each other, and access a vast array of resources such as websites, online services, and applications. The internet is based on a client-server model, where users access resources on the internet by connecting to a server using a device such as a computer or smartphone.**_

_**Or we can Simply Say , All machines around the world is interconnected. Something like this:**_

_****_

<figure><img src=".gitbook/assets/image (24) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Each Computer is given an address known as `IP Address.` An IP address is a unique address that identifies a device on the internet or a local network. IP stands for "Internet Protocol," and we are able to fetch data with the help of `IP Address.`
{% endhint %}

But there is a challenge, How would you fetch data from a Machine that is not switched on, or is not simply connected to internet? Then came **servers.**

### <mark style="color:purple;">Servers</mark>&#x20;

**On the World Wide Web, for example, a Web server is a computer that uses the HTTP protocol to send Web pages to a client's computer when the client requests them.**&#x20;

In simple words, Servers used to get Data from Computer A so that even if Computer A is not Connected , Server can send information to client's Computer.

<figure><img src=".gitbook/assets/image (1) (2) (2).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">Two Tier Servers :</mark>&#x20;

#### Application Tier Server :&#x20;

An application tier server is a type of server that is used to host and run application software. It is responsible for processing and managing requests from clients, such as web browsers or mobile devices, and delivering the appropriate responses. The application tier server communicates with databases and other back-end systems to retrieve and store data, and it also handles tasks such as authentication, authorization, and session management.

#### Data Tier Server :&#x20;

A data tier server is a type of server that is used to store and manage data. It is responsible for the physical storage, organization, and retrieval of data in a database or other data storage system. The data tier server is separate from the application tier server, which handles the processing and management of requests and responses. Data tier server is also responsible for ensuring the integrity, security and backup of the data.

<figure><img src=".gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">What is File System :</mark>&#x20;

A file system is a way for a computer's operating system to organize and keep track of files and folders on a storage device, such as a hard drive. It is responsible for storing, retrieving and updating files as well as managing the available space on the storage device.

Some common challenges in file systems include:

1. \--->**Scalability**: <mark style="color:red;">As the number of users and files increases, the file system must be able to handle the load and continue to function effectively.</mark>
2. \--->**Performance**: <mark style="color:red;">File systems must be able to access files quickly and efficiently, even when dealing with large amounts of data.</mark>
3. \--->**Data Consistency**: <mark style="color:red;">File systems must ensure that data is stored and retrieved consistently, even in the event of power failures or other system failures.</mark>
4. \--->**Data Security**: <mark style="color:red;">File systems must be able to protect data from unauthorized access and ensure data integrity.</mark>
5. \--->**Data Management**: <mark style="color:red;">File systems must be able to organize and manage large amounts of data in an efficient and effective manner.</mark>
6. \--->**Data Backup and Recovery**: <mark style="color:red;">File systems must be able to recover data in the event of data loss or corruption.</mark>
7. \--->**Concurrency and Access Control**: <mark style="color:red;">File systems must be able to handle multiple users accessing the same files at the same time and control access to files.</mark>
8. \--->**File system complexity and compatibility** : <mark style="color:red;">Handling different type of file systems and making them compatible with other systems.</mark>

One of the major problem we had to deal with is Organization. You can save data almost anywhere that makes accessing data , quite difficult.

<figure><img src=".gitbook/assets/image (1) (3).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:purple;">How Did We Solve This Problem ---> RDBMS (Relational Database Management System)</mark>

A Relational Database Management System (RDBMS) is a type of database management system that uses a relational model to organize data. It **stores data in tables, with each table consisting of rows and columns. The columns represent attributes of the data, and the rows represent individual records.**

**The RDBMS allows users to create, read, update and delete data in the database**. It also provides a way to enforce rules and constraints on the data to ensure the integrity and consistency of the data.

In simpler terms, **RDBMS is a type of software that helps organize, store and retrieve data in a structured way, like a digital spreadsheet. It allows you to create tables and specify relationships between different tables of data, making it easy to search and filter data based on specific criteria.**

<figure><img src=".gitbook/assets/image (1) (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
There are several tools available for working with Relational Database Management Systems (RDBMS).

Examples include Oracle SQL Developer, MySQL Workbench, and Microsoft SQL Server Management Studio.
{% endhint %}

### <mark style="color:purple;">Here Came SQL To Interact With RDMBS</mark> :&#x20;

**In simpler terms, SQL is a language that allows you to communicate with a database and retrieve, modify or add information to it. It is like a bridge between the user and the database.**

SQL (Structured Query Language) is a programming language that is used to manage and manipulate relational databases. It is used to insert, update, and query data stored in a relational database management system (RDBMS). SQL allows you to interact with the database by inserting, updating, and retrieving data stored in tables.

SQL is used to perform a variety of tasks, such as:

* Creating and modifying tables, views, and other database objects
* Inserting, updating, and deleting data in the database
* Retrieving data from the database using SELECT statements
* Creating and modifying indexes to improve the performance of queries
* Managing users and controlling access to the database
* Creating and managing constraints to ensure data integrity

**SQL is a standard language used by most RDBMS, like Oracle, MySQL, SQL Server, PostgreSQL, and SQLite, but there are slight variations and differ ent features implemented in each one.**

<figure><img src=".gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

Now different applications generate Data and server helps us to store them, what we need to do is to fetch data from Server and perform analysis with the help of pandas.

To run queries from SQL, we need to install **mysql-connector-python.**&#x20;

```python
pip install mysql-connector-python
```

So we are going to access data from cloud service **AWS(Amazon Web Sevices).**We are going to create a database first. we will import data from excel in our database.

<figure><img src=".gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

### **Things that we need to fetch data from a Relational Database :**&#x20;

&#x20;**--->RDBMS**

**--->IP Address**

**--->Server UserName**

**--->Server Password**

**--->Database**

**--->Table**

### Go to [AWS](https://aws.amazon.com/) :

Sign in or Create an account and Sign in AWS.

### Go to Services and Choose Database to Create One.

&#x20;Go to services and click on database and click on RDS (Relational Database Service).

<figure><img src=".gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/image (2) (3).png" alt=""><figcaption></figcaption></figure>

Here in resources you can see no DB Instances or any server is active as of now.  So let's create a new Database by clicking on **Create Database.**

<figure><img src=".gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

Choose **MySQL** engine. Hence RDBMS is **MySQL.**

Choose Template **Free tier.**

<figure><img src=".gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

Now go to settings below and fill all the required information. So we have created a database instance named **console-instance.**

<figure><img src=".gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Use endpoint in console-instance DB as IP , under Connectivity and security.&#x20;
{% endhint %}

\


<figure><img src=".gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

Now Let's create a connection with MySQL Workbench.

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

So we have created a connection named **dec-connect.**  Add **IP** as **Hostname** and **username** as **admin** and **Password** as we had set before.After this Click on **test the connection.**  A Pop up should appear something like this:&#x20;

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

After this we have successfully tested the connection and then click on **OK.** You will find SQL connections like this :&#x20;

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

**Click on dec-connect.  It will open SQL - Editor for you.**&#x20;

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

So let us create a Database on this Server First. To Create a Schema, Click on **sys** and then click on **create schema.**  So We have created a Schema named **consolebase.**

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

After Creating Schema, we need to create a table.  You can simply click in create table and create a table manually.

<figure><img src=".gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

Or we can directly import our excel file from import option , that is below **Table Data Import Wizard.**  Click on **Table Data Import Wizard** and Browse your File from there only.

<figure><img src=".gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Click on **Next.**

<figure><img src=".gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

Create a new table named **datatable.** And then Click on next and finish.

<figure><img src=".gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Now you can see with this following Query,all the records:&#x20;

```sql
select * from consolebase.datatable;
```

&#x20;****&#x20;

<figure><img src=".gitbook/assets/image (6) (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**We have Established the connection , created database and table and stored our Data in it.**
{% endhint %}

Now Let's Create Connection using mysql-connector-python and fetch the data from server.

```python
import pandas as pd
import mysql.connector as mc

#connect will take configurations and establish the connection from server.
myco = mc.connect (host="hostname", User="username", 
passwd= "pswd", database= "db name")

# SQL Query to select all records from Datatable.
q="select from datatable"

df= pd.read_sql (q, myco)

t=date.today ()

df.to_csv(fr'{str (t) }.csv')
```

It will store the Data in a CSV File with current Date.&#x20;

<figure><img src=".gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
