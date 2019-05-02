# Oracle-Live-SQL
Live SQL Database from Oracle

System Version - macOS Majove 10.14.4

Git Version - 2.20.1 (Apple Git-117)

Java Version -  "1.8.0_131"


Oracle Live SQL Worksheet

• Create a table

Tables are the basic unit that store data. We store company's data, employees information in tables, and we commonly name our table as employee_id, inventory, First name, Last name, varchar, date, type, element. The table can be constrainted and unconstraint. A data with Not Null is unconstraint. 

• Example of creating a table

create table EMPLOYEE {

empno       number
name        varchar2(50) not null, 
job         varchar2(50), 
manager     number,
hiredate    date, 
salary      number(7,2),
commision   number(7,2),
deptno      number,
constraint  pk_employees primary key (empno), 
constraint  fk_employees_deptno foreign key (deptno),
  reference DEPARTMENTS (deptno)
 
 • Create Triggers
 Triggers happen when the database are fired. In Oracle, procedural SQL is called a PL/SQL Block. PL stands for procedural language. When an INSERT, UPDATE, DELETE happen on a table. Triggers support systems and other database event on DATABASE and SCHEMA. 
 
 Here is an example using trigger using built in function to obtain a globally unique identifier or GUID.
 
 create or replace trigger DEPARTMENTS_BIU 
      before insert or update on DEPARTMENTS
      for each row.
 begin
      if inserting and :new.deptno is null hen new.deptno := to_number is null then 
      : new.deptno := to_nummber(sys_guid(),
        'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX';
      end if 
 end;
 /
 
 create or replace trigger EMPLOYEES-BIU 
      before insert or update on EMPLOYEES
      for each row
 begin
      if inserting and :new.empno is null then 
          :new.empno := to_number(sys_guid(),
             'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX');
       end if; 
      end;
  /
  
  • Insert Data
  
  Now we have created the tables. Because we have a parent child relationship. The DEPARTMENTS table as the parent table, and the EMPLOYEES table as the child table we will first INSERT a roll in the DEPARTMENTS table. 
  
  Example 
  
  insert into EMPLOYEES: 
  (name, job, salary, deptno) 
  values
  ('Sam Smith', 'Programmer'), 5000; 
  (select deptno 
  from departments 
  where name = 'Development'));
  
  Insert into EMPLOYEES: 
  (name, job, salary, deptno)
  values 
  ('Mara Martin', 'Analyst', 
  6000, 
  (select deptno)
  from departments
  where name = "Finance"));
  
  insert into EMPLOYEES 
  (name, job, salary, deptno);
  values
  ('Yun Yates', 'Analyst'), 
  5500, 
  (select deptno
  from dapartments)
  where name = 'Development; ));
  
  
  
       
