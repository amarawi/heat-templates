heat-templates
==============

OpenStack Heat templates for use on the 
[NeCTAR](http://nectar.org.au/) cloud for creating your own templates.

### How to use them
[Barebone](Barebone.yaml) is used to provide very essential parts of a normal Heat template. 

With above skeleton, adding diffent parts to a template. For example:
* manage services: [Fedora](Fedora_Barebone.yaml) or [CentOS](CentOS_Barebone.yaml) 
* [volume storage](Volume_CreateAttach.yaml)
* [cron job](Cronjob.yaml)
* [swifth client](Swift_Client.yaml)
* [manage config during the start-up](Configsets.yaml)

### Note 

For all templates with volume involvement, no matter if you want to keep
it or not, make sure volumes are: 
* unmounted 
* de-attached

before the deletion of a template. Fail to do so, the file system can be 
corrupted or volume is not usable. OpenStack Heat helpers do not take
care of these yet (Havana).

### Warning

Most templates are for demonstration. Therefore, they are very 
basic. So please check if the configuration suits to your needs 
especially *security*.
