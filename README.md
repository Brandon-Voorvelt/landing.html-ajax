# landing.html-ajax

*************************************************************
*******************	READ ME		*********************
*************************************************************

gist.github links:

landing.html 		: https://gist.github.com/Brandon-Voorvelt/b2d7f35004f91ad214f682719106d5bc
bookingForm.php 	: https://gist.github.com/Brandon-Voorvelt/e113f74350d9bb568c42f3943e024181
bookingForm.js		: https://gist.github.com/Brandon-Voorvelt/1fb72cfd553a673a3ed93ff631cdef3b
contactUsForm.php	: https://gist.github.com/Brandon-Voorvelt/c4c918acdbe8466ec3a79ed57ae7ebf5
contactForm.js		: https://gist.github.com/Brandon-Voorvelt/c064027121e589eef3d9ff1ba5f949c5


****************************************************************************************
**********************************************************************      landing.html
****************************************************************************************
1) In the <head> : jquery-3.6.0.js
2) At EOF : bootstrap.js / jqBootstrapValidation.js / bookingForm.js / contactForm.js

*Using PHP v7.1
*Using JQuery-3.6
*Mail servers are correctly configured and are working perfectly

------------------------------

 I have 2 HTML forms on my landing.html page
1) Form 1 - bookingForm	(Contains input & select option)
2) Form 2 - contactUsForm (Contains input & a textarea)

1)The purpose of the bookingForm, is to have the user complete the form and have the inputed data emailed 
	to a specified email address ( Email address ill be changed at a later stage) to booking the collection 
	/ delivery of a parcel. 
	This form works correctly and a HTML table with the data is emailed.

2)The purpose of the contactUsForm, is just simply let the user complete the general enquiry form and email
	this input to a specified email address (this will also change later).


I have used Bootstrap's tab layout so that the user can just click on the tab they would like, and that 
	specific form can be filled in.

--------------------------------------------------------------------------------------------------------
1)) bookingForm
	- Located in landing.html					--(public_folder)
	- Uses bookingForm.php for input validation & mail() function	--(Found in public_folder/forms)
	- Uses bookingForm.js for AJAX function, using JQuery 		--(Found in public_folder/js)
--------------------------------------------------------------------------------------------------------
2)) contactUsForm
	- Located in landing.html					--(public_folder)
	- Uses contactUsForm.php for input validation & mail() function --(Found in public_folder/forms)
	- Uses contactForm.js for AJAX function, using JQuery 		--(Found in public_folder/js)
--------------------------------------------------------------------------------------------------------

Going onto my landing.html file, the forms work correctly. The form is completed and input is validated 
	through the .php file and emailed off. BUT i do not want the user to be redirected to the .php file.
	So i am using JQuery's AJAX function to solve this problem. I have used almost identical files which
	work perfectly. 

The problem I am having, is that when I do not use my .js file - the form is validated and emailed off - but is redirected.
When i use my .js file, the "live" validation happens while filling in the form, but my submit button does not work.
***************************************************************************************
***************************************************************		bookingForm.php
***************************************************************************************

The bookingForm in landing.html's input ID's & name's match the variables below:
	$fName = $_POST['fName']; 	// Client First Name
	$lName = $_POST['lName'];	// Client Surname
	$phone = $_POST["phone"];	// Client Phone Number
	$email = $_POST["email"];	// Client Email Address 
	
	// Delivery Details
	$del_from = $_POST["del_from"];	// Collection Address
	$del_to = $_POST["del_to"];	// Delivery Address
	$del_type = $_POST["del_type"];	// Delivery Type = Economical / Next Day

	// Package Details
	$pac_q = 	$_POST["pac_q"];		//Package Quantity - Customer to give dimensions of largest package if > 1 !!
	$pac_size = 	$_POST["pac_size"];		//Package Width
	$pac_weight = 	$_POST["pac_weight"];		//Package Height
	$pac_frag = 	$_POST["pac_frag"];		//Package Fragile? Yes or No

1) I use the htmlspecialchars() when creating the variable
2) I then check none of the fields are empty and meet requirements 
3) If all fields have been completed, I filter the variables
4) The data is then mailed off using an HTML table.

***************************************************************************************
***************************************************************		contactUsForm.php
***************************************************************************************

The contactUsForm in landing.html's input ID's & names match the variables below:
	$fName =	 $_POST['c_fName'];
	$lName = 	 $_POST['c_lName'];
	$email_address = $_POST['c_email'];
	$phone = 	 $_POST['c_phone'];
	$message = 	 $_POST['c_message'];

Process is slightly different from bookingForm.php

1)I first check if the fields are empty
2) And validate the email field in the same process
3) Then assign the variables
4) And mail the data using a simple email
