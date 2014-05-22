heat-templates
==============

OpenStack Heat templates for use on the [NeCTAR](http://nectar.org.au/) cloud.

###What are they for
If you are just interested in installing packages, creating users, Heat
maybe is not worth much as you can script it more easily in
[user-data](http://docs.openstack.org/user-guide/content/user-data.html)
with nova or copy-paste on dashbarod. But if other Openstack resources
are required by your instance, Heat is better and worth investing time and effort.

###Why are there templates for different distros for the same purpose?
Different distributions (versions) have different commands to manage 
services or install packages. For example, when services need to be enable
or ensured, [Fedora](Fedora_Barebone.yaml) and [CentOS](CentOS_Barebone.yaml)
are different. Some commands have different paths on Ubuntu (not yet
supported by NeCTAR official image) to Red Hat like operating systems.
So consult relevant templates.

###How to use them
[Barebone](Barebone.yaml) is used to provide very essiential parts of a normal Heat template. 

With above skeleton, adding diffent parts to a template:
* manage services: [Fedora](Fedora_Barebone.yaml) or [CentOS](CentOS_Barebone.yaml) 
* [volume storage](Volume_CreateAttach.yaml)
* [cron job](Cronjob.yaml)
* [swifth client](Swift_Client.yaml)
* [manage config during the start-up](Configsets.yaml)
* [create a XFCE desktop environment](XFCE4.yaml). This template also can be used to compare the supports to XFCE by different distros.
* [create a Fedora XFCE spin](Fedora_XFCE4.yaml)

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
