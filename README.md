[![Quality Gate Status](https://community.objectscriptquality.com/api/project_badges/measure?project=intersystems_iris_community%2FJSONExport-ManyToMany-AD&metric=alert_status)](https://community.objectscriptquality.com/dashboard?id=intersystems_iris_community%2FJSONExport-ManyToMany-AD)  

# JSONExport-ManyToMany-AD
Sample for %JSONExport against a class with Many to Many Relationship   

This package was adopted from the [orphaned predecessor](https://openexchange.intersystems.com/package/JSONExportManyToMany)   
- fixed dockerfile to be version independent   
- fixed pending mapping of SuperServer   
- added support for IPM  
- added installation guide   
- added quality tag
- added demo server     
- enhanced README     

### Prerequisites    
Make sure you have [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and [Docker desktop](https://www.docker.com/products/docker-desktop) installed.    
### Installation   
Clone/git pull the repo into any local directory  

````    
git https://github.com/rcemper/JSONExport-ManyToMany-AD.git
````    
   
Build the container with your project:   

````
docker compose --progress plain build
````

Run the container

 ````
docker compose up -d
````
To follow the startup you may use

````
docker compose logs -f
````
### Testing  
After installing this sample, the following two commands can be run from terminal or console

````
docker-compose exec iris iris session iris    

do ##class(JSONExportManyToMany.TeacherStudent).Populate()         

do ##class(JSONExportManyToMany.TeacherStudent).Test()    
````
- The test output should appear as follows:

<pre>
{"Name":"Peter","Teachers":[{"ID":1,"Teacher":{"Name":"Teacher1Name"}},{"ID":2,"Teacher":{"Name":"Teacher2Name"}}]}
 
{"Name":"Nael","Teachers":[{"ID":3,"Teacher":{"Name":"Teacher1Name"}},{"ID":4,"Teacher":{"Name":"Teacher3Name"}}]}
 
{"Name":"Teacher1Name","Students":[{"ID":1,"Student":{"Name":"Peter"}},{"ID":3,"Student":{"Name":"Nael"}}]}
 
{"Name":"Teacher2Name","Students":[{"ID":2,"Student":{"Name":"Peter"}}]}
 
{"Name":"Teacher3Name","Students":[{"ID":4,"Student":{"Name":"Nael"}}]}
</pre>

You will notice here that when exporting from Student (First 2 output lines),    
the relationship to Teacher is followed through TeacherStudent and details of the Teacher are exported.    

Likewise, when exporting from Teacher, the relationship to Student is followed through    
TeacherStudent and details of the Student are exported.   

[Demo Server SMP](https://json-export-many-many.demo.community.intersystems.com/csp/sys/UtilHome.csp)    
[Demo Server WebTerminal](https://json-export-many-manyt.demo.community.intersystems.com/terminal/)   
