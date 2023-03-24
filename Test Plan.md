# <span style="color:white"> Test Plan </span>
Created by: Bryan Aguilar, Jacel Evangelista, Hunter Paul

## <span style="color:aqua"> UML Diagram </span>
<img src="UMLDiagram.jpg" width=60% height=60%>

### <span style="color:teal"> Description </span>
The Animal-R-Here sensors will detect sounds of animals and generate an alert to the park ranger terminal. From here 
the software will sound an audio alarm to get the attention of park rangers, then pull information from the California 
Park Database in order to creating a report detailing the sound type detected, location of the noise, and the date when 
it was detected. Afterwards the report will be stored in the database for future reference. When a park ranger logs on 
in order to disable the alarm and check the report, the system will match their credentials against the park ranger database
before allowing them to access a map api showing the report and the location of the detection.

#### <span style="color:teal"> Updates from Previous UML Diagram </span>
We removed a function from the AlarmSystem class and split it into the two location functions in the Alarm class as we felt that it would make more sense that way. We also changed the arrows heading out from the Alarm, ParkControl, and AnimalRHere classes in order to better reflect how they interact with the other classes.

## <span style="color:pink"> Test Set 1: Access to System </span>
This test is aimed at testing the access to the system specification of our software system. It will test specific units within the code, test the functional integrity of the software, and show the System/acceptance testing of logging into the system.

### <span style="color:salmon"> Test </span>
> Test Cases: 
>    - name: Jacel & Austin;
>    - user: JacelE & AustinZ; 
>    - password: CS250 & COMM100

<br />Unit Testing:
-  UserRanger.setname(string name); UserRanger.setuser(string user); UserRanger.setpass(string pass);
    -  This is the test if provided with no input will not be called and or logged into the system but if a user and pass is inputted it will then go to the checkID(); system.
    -  (e.g UserRanger.setname(JacelE, CS250);)
    -  (e.g) if no input given (UserRanger.setname(); -> default to “NULL”)
    -  If no input is given the program will graciously end as it will not be able to proceed without an ID or login info.
- UserRanger.getname(); UserRanger.getuser(); UserRanger.getpass();
    - This unit test gets the name, username, and password of the user.
- UserRanger.checkID();
    - Since this is a Boolean method it will search the database if it is a valid ID so it can be logged into the system.

> - UserRanger.setName(Jacel);
> - UserRanger.setuser(JacelE);
> - UserRanger.setpass(CS250);
> - UserRanger.getName();
> - UserRanger.getUser();
> - UserRanger.getpass();
> <br />Return(Jacel, JacelE, CS250);

<br />Funtional/Integration Testing:
- If valid login/ID
    > UserRanger.setname(JacelE, CS250); -> checkID(); -> login();->ACCESS TO SYSTEM
- If invalid login/ID
    > UserRanger.setname(AustinZ, COMM100); -> checkID(); ->UserRanger.setname();

An input of a login will start the program off by using such login to check if it’s valid and if it returns as true it will be logged into the system via the login() method. But if it to be returned false it will revert back to the start of the program and be asked to log in once more. Hence the functionality of such test works well together through asking for valid logins and not being let through to login() unless a valid ID is given hence working well together in unison.

<br />System Testing:

In System Testing the system will not be able to run if the proper login is not given. System testing the login is all determined if the login is valid and hence will successfully be able to start the system.

>    - Name: Jacel
>    - User: JacelE
>    - Password: CS250
>    - Login();
>    - ACCESS!#

This Test is aimed at covering the functionality of our system so it can properly access/login to the system. The unit testing of this program tests if a login is given and if it’s valid and if no input is given it will default to NULL so the program does not crash. The Functional/Integration Function of this System will shows how the functions of the login test works together from setting the username and password to checking if it is valid and lastly calling the login method to properly have access to the whole system. The System testing relies solely on the login() method to therefore have access to the system.


## <span style="color:pink"> Test Set 2: Alarm Report System </span>
These tests are aimed at testing the alarm triggering and report generation part of the system. They will test specific units within the code, ensure the functions integrate correctly with one another, and test to check if the overall system works well with the code.

### <span style="color:salmon"> Test 1: Alarm Generation </span>
Unit Testing:
  - getName(); setName(string name);
    - This test will ensure that the getter and setter of the alarm name functions properly, both getting the name of the alarm as well as setting the name when creating a new alarm
  - addMap();
    - This will check to ensure that map generation is functioning correctly within the class, creating a map of where the alarm was triggered in the park
  - getTime(); setTime(double time);
    - This test will test the functionality of the sotring of time in addition to setting it. The getTime() function will return the time the alarm was triggered, and the setTime() function will set the time at which the alarm was triggered
  - getLocation(); setLocation(long coord);
    - This test will verify that the alarm location is properly retireved when calling the getter, as well as ensuring that the location process functions as intended when giving the setter a designated degree where the alarm is located
  
> Alarm:
>   - setName("Test 1"); 
>   - setTime(23.42); 
>   - setLocation(12345); 
>   - addMap(); 
>   - getName(); 
>   - getTime(); 
>   - getLocation(); 

<br />Functional Testing:
  - AlarmSystem
    - The AlarmSystem class interacts with the alarm class by managing the creation and turning off of alarms. This test will make sure that the Alarm class is properly intialized and capable of being able to interact with the other classes in the software by creating instances of its class as well as disabling those instances when they are active.

> createAlarm(); 
> <br />resolveAlarm();

<br />System Testing:
  - Map Class Interaction
    - The Alarm system, when triggered, is coded to create an audio alarm in order to alert park rangers, as well as generate a report on the map showing which alarm was triggered in addition to its report. This test will be performed to ensure that the end goal functionality of the alarm system is working as intended by creating a map prompt for the ranger to see.

>  Map Test:
>   - createAlarm(); 
>   - setName("Map Test"); 
>   - setLocation(12345); 
>   - addMap(); 
>   - send false alarm trigger
>   - check if map has been populated with alarm data


### <span style="color:salmon"> Test 2: Report Creation </span>
Unit Testing:

> Alarm --> (String: name, double: time, long: location, sound, String: AlertType) --> double getTime()
>   - Alarm.getTime(...)

The Alarm class's main purpose is to create the alarm itself. In this case, we will be
testing the getTime() function. The getTime() function is tasked to get the time at which
the alarm was set off. In order to do this the function will take a double as a parameter
and return that exact same double to the setTime() function. For instance, if the alarm
went off at 17.30 the getTime() function will take 17.30 as its parameter and retrieve its
value; so that it can be accessed by the setTime() function.

> Alarm.getTime(double time)
>   - return 17.30 

<br />Functional Testing:

> AlarmSystem & Alarm --> (String: detectionType, Alarm(): alert) --> void createAlarm(), boolean resolveAlarm()
> - AlarmSystem.createAlarm(...)

In the AlarmSystem class, the user can turn off the alarm and create an alarm. In this
case, we are testing the createAlarm() function which creates and stores the alarm in
the database. For this function to work, it must take in two parameters which are
detectionType and alert. The alert parameter is an object from the Alarm class and
detectionType is the string that explains the type of detection the user has categorized
the detection to be. For example, an alarm goes off at 3.00, it is located in the northern
part of the national park, and the sensor that detected the sound is called “Delta.” The
ranger reviews the detection and categorizes it as a “suspected” detection. The
createAlarm() method combines the information from the Alarm class with the ranger's
classification of the detection.

> AlarmSystem.createAlarm(Alarm alert, String detectionType)
>   - Time: 3:00 am
>   - Location: 11011°
>   - Sensor: Delta
>   - Detection Type: Suspected

<br />System Testing

> userRanger --> ControlSystem --> Alarm --> AlarmSystem --> Report

For the system testing, we will be seeing if the process of logging in and accessing the
reports work. In order for this process to start the user must have access to the system,
if the user has access he will then be sent to the ControlSystem() class. In the control
system, the user will have control of the full system, however, in this scenario the user is
turning off and categorizing the alarm that was set off. Afterward, he will be sent to the
Report() class, where he can view the reports in chronological order. This is a great
example of a testing scenario: Ranger #1827, with username "ranger7" and password
"Peanut2003", has categorized the alarm Delta as "suspected" and is asking to view its
report. The system will go through both the login() and checkID() functions and return
true. Giving him access to the control system he will then turn off the alarm which will
make the function resolveAlarm() return false and the createAlarm() method will
combine both sensor and classification information and store it in the database. Lastly,
udder will be sent to the Report() class where the function sort() will store each report in
chronological order in a vector and display with the display() method.

> Login:
>   - Username: ranger7, Password: Peanut2003, ID#1827
> Alarm:
>   - Time: 3:00 am
>   - Location: 11011°
>   - Sensor: Delta
>   - Detection Type: Suspected
> Reports:
>   - Jan 31, 2023 / 12:00 pm / Sensor: Comic / Location: 10001° / Type: Definite
>   - Feb 21, 2023 / 15:12 pm / Sensor: Bravo / Location: 11111° / Type: Definite
>   - Mar 24, 2023 / 3:00 am  / Sensor: Delta / Location: 11011° / Type: Suspected

These tests are aimed at covering the functionality of the alarm system, including its handling by the AlarmSystem class, report generation, and interaction with the map. The unit tests aim at ensuring that the individual functions of the Alarm class are functioning correctly so that report generation and map population are able to access the functions they need in order to run. The integration tests aim at ensuring that the Alarm class can be properly accessed and interacted with by the AlarmSystem class, which is what handles report generation and map population. The system tests are aimed at ensuring that the alarm system runs uninterrupted from issues during its pathing from the Alarm class, all the way to its end goals in the Report class and MapSystem class.