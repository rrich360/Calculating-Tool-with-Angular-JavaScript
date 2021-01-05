# Calculating-Tool-with-Angular-JavaScript
This Calculating Application calculates the cost of energy usage per year in Kilowatts between different light bulbs 

# Declaring the Angular Application

/* Starting this JavaScript file as this function so that this particular function can exist with other JavaScripts */

/* The function inside the brackets is being defined to declare the Angular application in the HTML */

/* Below are the two main elements that define the Angular App */

/* Declaring the variable app to be the name 'myCalculator'*/



 	(function(){
	var app = angular.module('myCalculator', []);
	}

	
	
  
  # Calculator Controller
  
	/* Adding the controller.. which is named 'CalculatorController' has a Angular service called scope */
	/* Using the scope service allows me to share variables between Javascript file and the HTML file	*/
	
  
	 	app.controller('CalculatorController',['$scope',function($scope){

 	$scope.lumen_options = [375, 600, 900, 1125, 1600];
 	$scope.current_lumens = 600;
 	$scope.current_cost = 13;
 	$scope.current_hours = 4;
 	$scope.total_days = 365;

# Conversion to calculate cost

	/* In this portion of the function, a conversion is used to help calculate the cost to operate a light bulb */
		
		$scope.inc_conversion = .0625;
		$scope.hal_conversion = .0450;
		$scope.cfl_conversion = .0146;
		$scope.led_conversion = .0250;
		
		# Define function inside scope to calculate values
    
	/* In this portion, you have to define the function on the scope inside the controller */
	
	/* Creating a new variable for wattage ($scope.inc_wattage) to calculate set of values for wattage */	
	
	/* Also, use 'toFixed' function to set values to 1 decimal place */
	
		$scope.calculate = function () {
 			
 			$scope.inc_wattage = ($scope.current_lumens * $scope.inc_conversion).toFixed(1); 
 			$scope.hal_wattage = ($scope.current_lumens * $scope.hal_conversion).toFixed(1);
 			$scope.cfl_wattage = ($scope.current_lumens * $scope.cfl_conversion).toFixed(1);
 			$scope.led_wattage = ($scope.current_lumens * $scope.led_conversion).toFixed(1);

		
	/* This portion includes a set of calculations that will calculate the price */
	
	/* Need to set a conditional statement to prevent users from entering more than 24 hours in a day */	
		
		
 		if( $scope.current_hours > 24){ $scope.current_hours = 24; }


		
# Setting variable for calculating current number of hours times total number of days
	

 	var total_hours = $scope.total_days * $scope.current_hours;
 	var cost = $scope.current_cost / 100;

		
# Calculate total energy usage

	/* In this final portion, we will multiply wattage by total number of hours to calculate energy usage */
	
	/* Since we need to come up with price per year to operate light bulb we will multiply wattage by 365 */
	
	/* Wattage is always in kilowatt hours so we use 1000 as the constant value */
	
	/* In these values, the decimal function will be set to 2 decimal places */
	
	/* lets pretend the user wants to produce 600 lumens (lm). therefore, we multiply that value by the conversion rates given. */
	
	
	 	$scope.inc_cost = ((($scope.inc_wattage * total_hours) / 1000) * cost).toFixed(2);
 	$scope.hal_cost = ((($scope.hal_wattage * total_hours) / 1000) * cost).toFixed(2);
 	$scope.cfl_cost = ((($scope.cfl_wattage * total_hours) / 1000) * cost).toFixed(2);
 	$scope.led_cost = ((($scope.led_wattage * total_hours) / 1000) * cost).toFixed(2);	

 	}
			$scope.calculate();
		}])
		
		})();



	

