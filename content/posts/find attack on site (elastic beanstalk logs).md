---
title: "find attack on webpage"

## Steps for find attack
If someone going to attack the website then go to aws elastic beanstalk logs and check access logs
under the logs There should be some unknown scripts running like this “GET /login HTTP/1.1" 200 31”
If find something like that then block the ip using vpc acls 
Open vpc 
Select the vpc which you are using
And open network ACLs
And add an inbound rule there
Give rule add port and specific IP which is trying to do something wrong.


