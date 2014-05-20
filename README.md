heat-templates
==============

OpenStack Heat templates for use on the [NeCTAR](http://nectar.org.au/) cloud.

Different distributions (versions) have different commands to manage 
services or install packages. Some commands have different paths on 
Ubuntu (not yet supported by NeCTAR official image) and Red Hat like 
operating systems. So consult relevant templates.

###How to use them
[Barebone](Barebone.yaml) is used to provide very essiential parts of a normal Heat template. 

When services need to be enable or ensured, [Fedora](Fedora_Barebone.yaml) and [CentOS](CentOS_Barebone.yaml) are different.

With above skeleton, adding diffent parts to a template:
* [volume storage](Volume_CreateAttach.yaml)
* [cron job](Cronjob.yaml)
* [swifth client](Swift_Client.yaml)
* [manage config during the start-up](Configsets.yaml)
* [create a XFCE desktop environment](XFCE.yaml). This template also can be used to compare the supports to XFCE by different distros.
* [create a Fedora XFCE spin](Fedora_XFCE.yaml)

###Note 

For all templates with volume involvement, either it is 
mounting an existing or keeping volume after a stack is deleted, 
make sure volumes are: 
* umounted 
* de-attached

before the deletion. Fail to do so, the file system can be 
corrupted. OpenStack Heat helpers do not take care of these yet 
(Havana).

###Warning

Most templates are for demonstration. Therefore, they are very 
basic. So please check if the configuration suits to your needs 
especially *security*.
