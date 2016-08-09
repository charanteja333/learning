# Learning postgresql

* `psql` -- to login into postgre shell
*  `/?` -- For help in psql shell
*  `\connect <databasename>` -- To connect to a given database
*  `\d` -- list tables in a database
*  `\l` -- Will list all the databases in a machine
*  `\h` -- Command help
*  `\q` -- To quit psql
*  `psql -U <user name> -h <machine name> -d <database name> -w <password> -p <port>` -- To login into a postgres database
*  `psql -U <user name> -h <machine nname> -W` -- Will try to login without password
* `pg_dumpall > <name of backup file>` -- postgres backup is taken into the file
*  `drop database <dbname>` -- Will drop the database
* `createdb --encoding=’utf-8’ -template=template0 <dbname>;`  or `createdb -E utf-8 -T ‘template0’ <dbname>;`- will create the database with given endocind   
*  `psql -d <dbname> -f <db backup file>` -- Will restore the database from the backup file


> **Sample psql commands** :    
/usr/sbin/chroot /opt/id/epsilon su - epsilon -c "psql -P pager=off
--pset footer -H -z -c \"select row_number() over (ORDER BY created) as
SrNo,name,created,createdby,lastmodified,lastmodifiedby from task where
t_type='WORKFLOW' and deleted='f' and created::date >= Now()::date-7 order
by created;\""

**Sample postgresql queries**

select collection.name from collection,object_collection where collection.id=object_collection.collection and object_collection.object_type='Workflow';

*Workflows not executed in last 60 days*

select name from task where t_type='WORKFLOW' except select distinct task.name from task,task_runlog where task.id=task_runlog.task_id and task.t_type='WORKFLOW' and task_runlog.started::date >=Now()::date-60

*Workflows executed in last 60 days*

select name from task where t_type='WORKFLOW' intersect select distinct task.name from task,task_runlog where task.id=task_runlog.task_id and task.t_type='WORKFLOW' and task_runlog.started::date >=Now()::date-60

*List of workflows in epsilon*

select name from task where t_type='WORKFLOW'

*Modified workflow report*

select row_number() over (ORDER BY t1.lastmodified) as Srno, t1.name,t1.created,t1.createdby,t1.lastmodified,t2.lastmodifiedby from task t1,task t2  where t1.deleted='f' and  t1.lastmodified IN (t2.lastmodified,t2.created) and t1.t_type='WORKFLOW' and t2.t_type!='WORKFLOW' and  t1.lastmodified::date >= Now()::date-7 order by t1.lastmodified;

*Duplicate entries for workflow*

select row_number() over (ORDER BY t1.lastmodified) as Srno, t1.name,t1.created,t1.createdby,t1.lastmodified,t2.lastmodifiedby from task t1,task t2  where t1.deleted='f' and  t1.lastmodified IN (t2.lastmodified,t2.created)  and t1.t_type='WORKFLOW'  and  t1.lastmodified::date >= Now()::date-7 order by t1.lastmodified;

*Detailed to the task level*

select p.name as ParentName,p.t_type as ParentType,t.name as ChildName,t.t_type as ChildType,t.created,t.createdby,t.lastmodified,t.lastmodifiedby from task p inner join task t on p.id=t.parent where t.deleted='f' and t.lastmodified::date >= Now()::date-1 union select name as ParentName,t_type as ParentType,name as Childname,t_type as ChildType,created,createdby,lastmodified,lastmodifiedby from task where t_type='WORKFLOW' and deleted='f' and lastmodified::date >= Now()::date-1 order by lastmodified;
 
 