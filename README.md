# project1.2

1. 
titanic = LOAD '/user/flume/tweets/TitanicData.txt' using PigStorage(',') AS (pid:int,survived:int,pclass:int,name:chararray,sex:chararray,age:int,sibsp:int,par:int,tkt:chararray,
fare:float,cabin:chararray,empark:chararray);
dump titanic;
grouped   = GROUP titanic  by pclass;
avg       = foreach grouped generate AVG(titanic.fare);
dump avg

2. filter_people = filter titanic by empark = 's' AND survived = 0;
   num_group = GROUP filter_people by plcass;
   num_count = foreach num_group generate group,COUNT(*);

3. filter_died = filter titanic by survived = 1;
   num_group = GROUP filter_people by (plcass,sex);
   num_count = foreach num_group generate group,COUNT(*);
