# Learning chef

###Chef is configuration management tool
 
> Chef architecture has a chef server, chef work station and chef nodes. Cookbooks contains recipes which in turn contains scripts to install/configure the servers.   
>  Chef nodes are the end points/servers to be managed. Chef work station is used to write cookbooks and upload the same to chef server using knife utility.     
>  Cookbooks can contains multiple recipes which can have dependencies on other cook books.   
>  Chef nodes syncronizes with the chef server to keep up to date configuration settings and not the other way.    
>  Chef nodes must be installed with chef client which can be done using knife boot strap method from chef work station
 

* `curl -L https://www.opscode.com/chef/install.sh | sudo sh` -- Install chef client
* `knife cookbook site download <cookbookname>` -- Will download the cookbook from chef super market
* `chef-client -z -o <cookbookname>` -- Will run the chef client in chef-zero mode and run the given cookbook name
