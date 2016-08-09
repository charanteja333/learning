#Learning Salt

* To install salt first salt PPArepo needs to be added.

`sudo apt-get install python-software-properties`
`sudo add-apt-repository ppa:saltstack/salt`

* It can also be installed `curl -L https://bootstrap.saltstack.com -o install_salt.sh` from salt boot strap method. `sudo sh install_salt.sh -P -M` will install all the required 

* Execute `sudo apt-get update`
* Install salt minion or master 

`sudo apt-get install salt-master`
`sudo apt-get install salt-minion`

* Config for master or minion is in path `/etc/salt/master` and `/etc/salt/minion`

* Salt listens on port `4505` and `4506` . Create directories `mkdir -p /srv/salt && mkdir -p /srv/pillar` . To restart master `service salt-master restart`

* Edit master in minion config to set the master ip address to communicate to salt. Restart `service salt-minion restart` after any config changes

* To list all the minions in a salt master execute `salt-key -L`
*  To check the key on a minion `sudo salt-call key.finger --local` will give the key
*  To cross check the key of minion on salt master `sudo salt-key -f <miniond>` can be used
*  `sudo salt-key -a <minion>` to accept the key of minion. `salt-key -A` will accept all the pending minion keys
*  `sudo salt '<minion>' test.ping` to ping a salt minion
*  `salt <minion> pkg.install nginx` to install nginx package on minion from salt server and restart `salt <minion> service.start nginx` 
*  Managing each infra by running individual commands is difficult. So salt has a concept called formulaes.
* A yaml file in below mentioned structure and names as install_git.sls can be used to run 

>

install_git:
  pkg:
    - installed
    - pkgs:
      - git
      

* salt formulaes can be executed using `salt <minion> state.sls install_git` . Similarly all formulae can be executed as `salt <minion> state.sls install_git,vim,webserver`.
* To apply salt formulae dynamically a concept of high state is available in salt. when command `salt <minion> state.highstate` is executed minion will get the file `top.sls` from `/srv/salt/` directory and run on the minion based on the details provided. top.sls structure is as follows:


 base:
  '*':
    - vim
  'minion*':
    - git
    - webserver
  'minion02':
    - mongodb 
    
* From the above all the minions will have vim formulae run and so on. Default is base environment
* `salt <minion> disk.usage` -- Will give the disk usage details of the salt