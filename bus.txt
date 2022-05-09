create table bus(bus_no number(3) primary key,source varchar(10),destination varchar(10),couch_type varchar(20));
create table reservation(pnr_no number(3) primary key,journy_date date,no_of_seat number(3),address varchar(20),contact_no number(15),bus_no number(3) references bus(bus_no),seat_no number(3));
create table ticket(ticket_no number(3) primary key,journy_date date,age number(3),sex varchar(10),source varchar(10),destination varchar(10),dep_time varchar(10),bus_no number(3));
create table passenger(pnr_no number(3) primary key,ticket_no number(3) references ticket(ticket_no),name varchar(10),age number(3), sex varchar(10),contact_no number(15));
create table cancellation(pnr_no number(3) primary key,journy_date date,seat_no number(3),contact_no number(15));

desc bus;

 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 BUS_NO                                    NOT NULL NUMBER(3)
 SOURCE                                             VARCHAR2(10)
 DESTINATION                                        VARCHAR2(10)
 COUCH_TYPE                                         VARCHAR2(20)

desc reservation;

 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 PNR_NO                                    NOT NULL NUMBER(3)
 JOURNY_DATE                                        DATE
 NO_OF_SEAT                                         NUMBER(3)
 ADDRESS                                            VARCHAR2(20)
 CONTACT_NO                                         NUMBER(15)
 BUS_NO                                             NUMBER(3)
 SEAT_NO                                            NUMBER(3)

desc ticket;

 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 TICKET_NO                                 NOT NULL NUMBER(3)
 JOURNY_DATE                                        DATE
 AGE                                                NUMBER(3)
 SEX                                                VARCHAR2(10)
 SOURCE                                             VARCHAR2(10)
 DESTINATION                                        VARCHAR2(10)
 DEP_TIME                                           VARCHAR2(10)
 BUS_NO                                             NUMBER(3)

desc passenger;

 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 PNR_NO                                    NOT NULL NUMBER(3)
 TICKET_NO                                          NUMBER(3)
 NAME                                               VARCHAR2(10)
 AGE                                                NUMBER(3)
 SEX                                                VARCHAR2(10)
 CONTACT_NO                                         NUMBER(15)

desc cancellation;

 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 PNR_NO                                    NOT NULL NUMBER(3)
 JOURNY_DATE                                        DATE
 SEAT_NO                                            NUMBER(3)
 CONTACT_NO                                         NUMBER(15)






insert into bus values(200,'kollam','kozhicode','sleeper seat');
insert into bus values(201,'palakkadu','tvm','sleeper seat');
insert into bus values(202,'chenni','karapakkam','ac');
insert into bus values(203,'eranakulam','kannur','semi sleeper seat');
insert into bus values(204,'tvm','kozhicode','sleeper seat');

select * from bus;

    BUS_NO SOURCE     DESTINATIO COUCH_TYPE
---------- ---------- ---------- --------------------
       200 kollam     kozhicode  sleeper seat
       202 chenni     karapakkam ac
       203 eranakulam kannur     semi sleeper seat
       204 tvm        kozhicode  sleeper seat
       201 palakkadu  tvm        sleeper seat


insert into reservation values(100,'1-nov-2000',1,'anad',1234567890,200,2);
insert into reservation values(101,'2-feb-2000',2,'kollam',1234562190,201,3);
insert into reservation values(102,'3-mar-2000',3,'kochi',1234563490,202,4);
insert into reservation values(103,'4-dec-2000',4,'kozhicode',1234564590,203,4);

    PNR_NO JOURNY_DA NO_OF_SEAT ADDRESS              CONTACT_NO     BUS_NO     SEAT_NO
---------- --------- ---------- -------------------- ---------- ----------  ----------
 

       100 01-NOV-00          1 anad                 1234567890        200     2
       101 02-FEB-00          2 kollam               1234562190        201     3
       102 03-MAR-00          3 kochi                1234563490        202     4
       103 04-DEC-00          4 kozhicode            1234564590        203     4
         

insert into ticket values(300,'10-jan-2020',20,'male','kollam','kottayam','10 pm',200);
insert into ticket values(400,'1-feb-2020',21,'male','kottayam','kollam','12 pm',201);
insert into ticket values(500,'1-mar-2020',30,'female','kannur','kollam','11 pm',202);
insert into ticket values(600,'11-apr-2020',45,'female','tvm','kannur','12 pm',203);
insert into ticket values(700,'13-dec-2020',35,'female','delhi','chennai','1 pm',204);

select * from ticket;

 TICKET_NO JOURNY_DA        AGE SEX        SOURCE     DESTINATIO DEP_TIME   BUS_NO  
---------- --------- ---------- ---------- ---------- ---------- --------------------

       300 10-JAN-20         20 male       kollam     kottayam   10 am     200
       400 01-FEB-20         21 male       kottayam   kollam     11 am     201
       500 01-MAR-20         30 female     kannur     kollam     11 pm     202
       600 11-APR-20         45 female     tvm        kannur     12 pm     203
       700 13-DEC-20         35 female     delhi      chennai    1  pm     204
      
       
insert into passenger values(400,300,'shah',20,'male',1234554323);
insert into passenger values(401,400,'shahina',21,'female',1234554344);
insert into passenger values(402,500,'sarath',35,'male',1234554329);
insert into passenger values(403,600,'janu',19,'female',1234554321);
insert into passenger values(404,700,'ram',40,'male',1234554345);

select * from passenger;

    PNR_NO  TICKET_NO NAME              AGE SEX        CONTACT_NO
---------- ---------- ---------- ---------- ---------- ----------
       400        300 shah               20 female     1234554323
       401        400 shahina            21 male       1234554344
       402        500 sarath             35 female     1234554329
       403        600 janu               19 male       1234554321
       404        700 ram                40 female     1234554345


insert into cancellation values(600,'2-jan-2020',1,1234567890);
insert into cancellation values(601,'9-feb-2020',1,1234567878);
insert into cancellation values(602,'8-mar-2020',1,1234567834);
insert into cancellation values(603,'7-nov-2020',1,1234567845);
insert into cancellation values(604,'10-oct-2019',2,1234432123);

select * from cancellation;

    PNR_NO JOURNY_DA    SEAT_NO CONTACT_NO
---------- --------- ---------- ----------
       600 02-JAN-20          1 1234567890
       601 09-FEB-20          1 1234567878
       602 08-MAR-20          1 1234567834
       603 07-NOV-20          1 1234567845
       604 10-OCT-19          2 1234432123


a. display ticket number and name of all passengers.
	select ticket_no,name from passenger;
		
 TICKET_NO NAME
---------- ----------
       300 shah
       400 shahina
       500 sarath
       600 janu
       700 ram

b.display all male passengers.
	select * from passenger where sex='male';

    PNR_NO  TICKET_NO NAME              AGE SEX        CONTACT_NO
---------- ---------- ---------- ---------- ---------- ----------
       401        400 shahina            21 male       1234554344
       403        600 janu               19 male       1234554321

c.find the names of the passenger whose age is between 20 and 40.
	select name ,age from passenger where age between 20 and 40;

NAME              AGE
---------- ----------
shah               20
shahina            21
sarath             35
ram                40

g.find all the passenger who cancelled ticket on 10.10.2019.
	select * from cancellation where journy_date='10-oct-2019';

    PNR_NO JOURNY_DA    SEAT_NO CONTACT_NO
---------- --------- ---------- ----------
       604 10-OCT-19          2 1234432123

h.display the sorted list nof passenger name.
	select count(sex) from ticket where bus_no=200;


COUNT(SEX)
----------
         1

i.display the sorted list of passenger names.
	select * from passenger order by name asc;


    PNR_NO  TICKET_NO NAME              AGE SEX        CONTACT_NO
---------- ---------- ---------- ---------- ---------- ----------
       403        600 janu               19 male       1234554321
       404        700 ram                40 female     1234554345
       402        500 sarath             35 female     1234554329
       400        300 shah               20 female     1234554323
       401        400 shahina            21 male       1234554344

j.find the ticket number of passenger whose name starts with 's' and ends with 'h'.
	select name,ticket_no from passenger where name like 's%h';

NAME        TICKET_NO
---------- ----------
shah              300
sarath            500       
