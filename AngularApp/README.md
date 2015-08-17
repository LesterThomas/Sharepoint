# Angular Application in Sharepoint

This is a very simple Angular application using the Sharepoint REST API to pull data from Sharepoint and displaying them in a list.

The simple list has 3 sections:

1. Load the angular framework

```
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.2/angular.min.js"></script>   
```

2. Javascript application and controller that builds the model into the $scope variable.

This example displays the list `CSMMasterList`: It is possible to display any list using this mechanism. The full set of lists is available at the `/_vti_bin/ListData.svc/` URL.

```
<script>   
 

	var myAngApp = angular.module('SharePointAngApp', []);   
	
	myAngApp.controller('spServicesController', function ($scope, $http) {   
	$http(
		{   
			method: 'GET',   
			url: "/group/systems%20architecture/_vti_bin/ListData.svc/CSMMasterList",   
			headers: { "Accept": "application/json;odata=verbose" }   
		}
		).success(function (data, status, headers, config) { 

			$scope.services = data.d.results;  
			
		}).error(function (data, status, headers, config) {   
		  console.log(status);
		});  
    }); 
	

</script>  
```


3. HTML View that links to the angular application `SharePointAngApp` and controller `spServicesController` and displays the HTML table.

```
<div ng-app="SharePointAngApp" class="row">   
    <div ng-controller="spServicesController" > 
		<h1>CSM Master list</h1> 
        <table  >   
            <tr>   
                <th class="ms-vh2">Ref</th>   
                <th class="ms-vh2">Service Name</th> 
                <th class="ms-vh2">Operation</th> 
                <th class="ms-vh2">Platform</th> 				
                <th class="ms-vh2">Comments</th>          
            </tr>   
            <tr ng-repeat="service in services">   
                <td class="ms-vb2">{{service.Ref}}</td>   
                <td class="ms-vb2">{{service.ServiceName}}</td>
				<td class="ms-vb2">{{service.ServiceOperation}}</td>                 
				<td class="ms-vb2">{{service.Platform}}</td>   
                <td class="ms-vb2">{{service.Comments}}</td>   
            </tr>   
        </table>   
    </div>   
</div> 
```







