heat-templates
==============

OpenStack Heat templates for use on the [NeCTAR](http://nectar.org.au/) cloud.

Different distributions (versions) have different commands to manage 
services or install packages. Some commands have different paths on 
Ubuntu (not yet supported by NeCTAR official image) and Red Hat like 
operating systems. So consult relevant templates.

###Note 

For all templates with volume involvement, either it is 
mounting an existing or keeping volume after a stack is deleted, 
make sure volumes are: 
* umounted 
* de-attached

before the deletion. Fail to do so, the file system can be 
corrupted. OpenStack Heat helpers do not take care of these yet 
(Havana).
