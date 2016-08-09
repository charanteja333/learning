#Learning Mongo


* `mongo` -- to enter the mongo shell
* `show dbs` -- to list the database 
* `use <dbname>` -- to connect the given db name
* `show collections` -- list the collections in a database
* `help` -- To get the mongo db help
* `db.help()` -- To get the db function help
* `ls(),pwd()` -- will work from mongo shell
* `db.<collectionname>.find()` -- Will return contents of a collection
* `db.<collectionname>.find({"<column name>":"<value>"})` -- Filter based on the values provided
* `db.<collection name>.remove({“<column name>”:”<value>”})` -- Will delete all the contents matching the criteria
* `db.<collection name>.remove({“<column name>”:”<value>”},{“justone”:true})` -- Will delete only first occurance matching the criteria
* `db.<Collection name>.drop()` -- Will drop the table
* `db.<collection name>.insert()` -- Will insert the table
* `db.<Db name>.drop()` -- Will drop the database
* `db.<collection name>.update({"<columname>":"<matchingvalue>"},{$set:{"<columnvalue>":"<newvalue>"}})` -- To update value on collection