###Learning

##### HA proxy

* [HA proxy architecture](http://www.haproxy.org/download/1.2/doc/architecture.txt)
* [HA proxy document](http://www.haproxy.org/download/1.2/doc/haproxy-en.txt)

##### Python-urllib

> 
import urllib2,base64   
request = urllib2.Request("`<url>`")     
KEY=“`<username>`”    
PASSWORD=“`<password>`”      
base64string = base64.encodestring('%s:%s' % (KEY, PASSWORD)).replace('\n', ‘')       
request.add_header("Authorization", "Basic %s" % base64string)      
result = urllib2.urlopen(request)     
op=result.read()       
oarg=“"     
for i in op:       
 if “-“ in i:       
  i=i.split(‘href=“‘)[1].split(‘/“‘)[0]      
  oarg=oarg+i+”,”       
print oarg     


