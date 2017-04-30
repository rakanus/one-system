# one-system
one-system , is a project for united all stadiums bookings in Saudi Arabia which fully funded by baratit company,
this version of webservices is (v1.0.0) which support these functions only :

- New Stadium Book 
- check availability by ( date - time range )
- Booking canceling by (Booking id)

# Requirements for API

* This API work under HTTP protocol only .
* All Request data must send by _GET only .
* All and every Request must contain authentication DATA , will provided by baratit .
* All Respone will be as JSON data only .
* All Request data must be in UTF-8 unicode.
* All Respone will be in UTF-8 unicode.

# API documentation 
The Test Environment of API is : 
``` 
test-one-system.baratit.com.sa
```

# (1) New Stadium Book 
This functions for make new book to particular Stadium at particular date and time-range .
- NOTICE: There are a charge for each Request with this function .
* Required Parameter
```
- FUNC = NEW_STADIUM_BOOK // to Selecet this function 
- API_USER & API_PASS  // authentication DATA
- STADIUM_ID // the number ID of STADIUM that you want to make a book in
- BOOKING_DATE // the Date that you want to make a aboot at , must be as unix timestamp Example : 1489352400000 -> 12/3/2016
- BOOKING_TIME_RANGE_id // the id of the time range that you want to make a book at , from ( 1 to 5 ) only
- USER_PHONE // the Phone number of the user ( the booker ) Example:0555000000
- USER_NAME // the Full Name of the user ( the booker ) in Arabic or English

```

* Request Example 
- Request as HTTP with GET DATA
```
http://test-one-system.baratit.com.sa/API.php?API_USER=FIRST_APP&API_PASS=12345678&FUNC=NEW_STADIUM_BOOK&STADIUM_ID=33&BOOKING_DATE=1489352400000&BOOKING_TIME_RANGE_id=5&USER_PHONE=0555028400&USER_NAME=rakan
```
- AND Respone data will be (JSON)

```
{"SUCCESS":"true","MSG":" -0000- successful booking ","BOOKING_ID":4897}
```


# (2) check availability by ( date - time range )
This functions allows you to check the availability of booking to particular Stadium at particular date and time-range ,
Before make a book .
- NOTICE : the NEW_STADIUM_BOOK function alredy make a check before excuteing the booking . 
- NOTICE: There are NO ANY charge for this function .
* Required Parameter
```
- FUNC = CHECK_AVAILABILITY // to Selecet this function 
- API_USER & API_PASS  // authentication DATA
- STADIUM_ID // the number ID of STADIUM that you want to check 
- BOOKING_DATE // the Date that you want to check at , must be as unix timestamp Example : 1489352400000 -> 12/3/2016
- BOOKING_TIME_RANGE_id // the id of the time range that you want to check at , from ( 1 to 5 ) only

```

* Request Example 
- Request as HTTP with GET DATA
```
http://test-one-system.baratit.com.sa/API.php?API_USER=FIRST_APP&API_PASS=12345678&FUNC=CHECK_AVAILABILITY&STADIUM_ID=33&BOOKING_DATE=1489352400000&BOOKING_TIME_RANGE_id=3
```
- AND Respone data will be (JSON)

```
{"SUCCESS":"true","MSG":" -1111- This book is ALLOWED "}
```




# (3) Booking canceling by (Booking id)
This functions allows you to cancel a book .
- NOTICE: There are NO ANY charge for this function .
* Required Parameter
```
- FUNC = BOOKING_CANCELING // to Selecet this function 
- API_USER & API_PASS  // authentication DATA
- BOOKING_ID // the number ID of Booking that you want to cancel
```

* Request Example 
- Request as HTTP with GET DATA
```
http://test-one-system.baratit.com.sa/API.php?API_USER=FIRST_APP&API_PASS=12345678&FUNC=BOOKING_CANCELING&BOOKING_ID=4898
```
- AND Respone data will be (JSON)

```
{"SUCCESS":"true","MSG":" -2222- successful CANCELING "}
```

# (4) Master Board Check Availability by ( month )
This functions allows you to check the availability of booking to particular Stadium at particular month ,
Before make a book , will return All Availability and not Availability days and time-ranges for a month .
- NOTICE : the NEW_STADIUM_BOOK function alredy make a check before excuteing the booking . 
- NOTICE: There are NO ANY charge for this function .
- NOTICE: if "Availability" parameter is "true" means you can book this day with this time range , if is "false" means you can not book this one . 
* Required Parameter
```
- FUNC =  MASTER_BOARD_CHECK_AVAILABILITY // to Selecet this function 
- API_USER & API_PASS  // authentication DATA
- STADIUM_ID // the number ID of STADIUM that you want to check 
- MONTH // the month that you want to check at , must be from ( 1 to 12 ) only the year it's automatically the current year .

```

* Request Example 
- Request as HTTP with GET DATA
```
http://test-one-system.baratit.com.sa/API.php?API_USER=TEST&API_PASS=TEST&FUNC=MASTER_BOARD_CHECK_AVAILABILITY&STADIUM_ID=33&MONTH=2
```
- AND Respone data will be (JSON)

```
{"1":{"DATE":"2017-02-12","TIME_RANGE":"3","PaX":"LS0tLTIwMTctMDItMTIgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"false"},"2":{"DATE":"2017-02-1","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMSBBTkQgdGltZSByYW5nZSBpZCBpcyAx","Availability":"true"},"3":{"DATE":"2017-02-1","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMSBBTkQgdGltZSByYW5nZSBpZCBpcyAy","Availability":"true"},"4":{"DATE":"2017-02-1","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMSBBTkQgdGltZSByYW5nZSBpZCBpcyAz","Availability":"true"},"5":{"DATE":"2017-02-1","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMSBBTkQgdGltZSByYW5nZSBpZCBpcyA0","Availability":"true"},"6":{"DATE":"2017-02-1","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMSBBTkQgdGltZSByYW5nZSBpZCBpcyA1","Availability":"true"},"7":{"DATE":"2017-02-2","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMiBBTkQgdGltZSByYW5nZSBpZCBpcyAx","Availability":"true"},"8":{"DATE":"2017-02-2","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMiBBTkQgdGltZSByYW5nZSBpZCBpcyAy","Availability":"true"},"9":{"DATE":"2017-02-2","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMiBBTkQgdGltZSByYW5nZSBpZCBpcyAz","Availability":"true"},"10":{"DATE":"2017-02-2","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMiBBTkQgdGltZSByYW5nZSBpZCBpcyA0","Availability":"true"},"11":{"DATE":"2017-02-2","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMiBBTkQgdGltZSByYW5nZSBpZCBpcyA1","Availability":"true"},"12":{"DATE":"2017-02-3","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMyBBTkQgdGltZSByYW5nZSBpZCBpcyAx","Availability":"true"},"13":{"DATE":"2017-02-3","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMyBBTkQgdGltZSByYW5nZSBpZCBpcyAy","Availability":"true"},"14":{"DATE":"2017-02-3","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMyBBTkQgdGltZSByYW5nZSBpZCBpcyAz","Availability":"true"},"15":{"DATE":"2017-02-3","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMyBBTkQgdGltZSByYW5nZSBpZCBpcyA0","Availability":"true"},"16":{"DATE":"2017-02-3","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMyBBTkQgdGltZSByYW5nZSBpZCBpcyA1","Availability":"true"},"17":{"DATE":"2017-02-4","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItNCBBTkQgdGltZSByYW5nZSBpZCBpcyAx","Availability":"true"},"18":{"DATE":"2017-02-4","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItNCBBTkQgdGltZSByYW5nZSBpZCBpcyAy","Availability":"true"},"19":{"DATE":"2017-02-4","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItNCBBTkQgdGltZSByYW5nZSBpZCBpcyAz","Availability":"true"},"20":{"DATE":"2017-02-4","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItNCBBTkQgdGltZSByYW5nZSBpZCBpcyA0","Availability":"true"},"21":{"DATE":"2017-02-4","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItNCBBTkQgdGltZSByYW5nZSBpZCBpcyA1","Availability":"true"},"22":{"DATE":"2017-02-5","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItNSBBTkQgdGltZSByYW5nZSBpZCBpcyAx","Availability":"true"},"23":{"DATE":"2017-02-5","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItNSBBTkQgdGltZSByYW5nZSBpZCBpcyAy","Availability":"true"},"24":{"DATE":"2017-02-5","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItNSBBTkQgdGltZSByYW5nZSBpZCBpcyAz","Availability":"true"},"25":{"DATE":"2017-02-5","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItNSBBTkQgdGltZSByYW5nZSBpZCBpcyA0","Availability":"true"},"26":{"DATE":"2017-02-5","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItNSBBTkQgdGltZSByYW5nZSBpZCBpcyA1","Availability":"true"},"27":{"DATE":"2017-02-6","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItNiBBTkQgdGltZSByYW5nZSBpZCBpcyAx","Availability":"true"},"28":{"DATE":"2017-02-6","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItNiBBTkQgdGltZSByYW5nZSBpZCBpcyAy","Availability":"true"},"29":{"DATE":"2017-02-6","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItNiBBTkQgdGltZSByYW5nZSBpZCBpcyAz","Availability":"true"},"30":{"DATE":"2017-02-6","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItNiBBTkQgdGltZSByYW5nZSBpZCBpcyA0","Availability":"true"},"31":{"DATE":"2017-02-6","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItNiBBTkQgdGltZSByYW5nZSBpZCBpcyA1","Availability":"true"},"32":{"DATE":"2017-02-7","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItNyBBTkQgdGltZSByYW5nZSBpZCBpcyAx","Availability":"true"},"33":{"DATE":"2017-02-7","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItNyBBTkQgdGltZSByYW5nZSBpZCBpcyAy","Availability":"true"},"34":{"DATE":"2017-02-7","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItNyBBTkQgdGltZSByYW5nZSBpZCBpcyAz","Availability":"true"},"35":{"DATE":"2017-02-7","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItNyBBTkQgdGltZSByYW5nZSBpZCBpcyA0","Availability":"true"},"36":{"DATE":"2017-02-7","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItNyBBTkQgdGltZSByYW5nZSBpZCBpcyA1","Availability":"true"},"37":{"DATE":"2017-02-8","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItOCBBTkQgdGltZSByYW5nZSBpZCBpcyAx","Availability":"true"},"38":{"DATE":"2017-02-8","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItOCBBTkQgdGltZSByYW5nZSBpZCBpcyAy","Availability":"true"},"39":{"DATE":"2017-02-8","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItOCBBTkQgdGltZSByYW5nZSBpZCBpcyAz","Availability":"true"},"40":{"DATE":"2017-02-8","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItOCBBTkQgdGltZSByYW5nZSBpZCBpcyA0","Availability":"true"},"41":{"DATE":"2017-02-8","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItOCBBTkQgdGltZSByYW5nZSBpZCBpcyA1","Availability":"true"},"42":{"DATE":"2017-02-9","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItOSBBTkQgdGltZSByYW5nZSBpZCBpcyAx","Availability":"true"},"43":{"DATE":"2017-02-9","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItOSBBTkQgdGltZSByYW5nZSBpZCBpcyAy","Availability":"true"},"44":{"DATE":"2017-02-9","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItOSBBTkQgdGltZSByYW5nZSBpZCBpcyAz","Availability":"true"},"45":{"DATE":"2017-02-9","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItOSBBTkQgdGltZSByYW5nZSBpZCBpcyA0","Availability":"true"},"46":{"DATE":"2017-02-9","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItOSBBTkQgdGltZSByYW5nZSBpZCBpcyA1","Availability":"true"},"47":{"DATE":"2017-02-10","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMTAgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"48":{"DATE":"2017-02-10","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMTAgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"49":{"DATE":"2017-02-10","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMTAgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"50":{"DATE":"2017-02-10","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMTAgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"51":{"DATE":"2017-02-10","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMTAgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"52":{"DATE":"2017-02-11","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMTEgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"53":{"DATE":"2017-02-11","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMTEgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"54":{"DATE":"2017-02-11","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMTEgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"55":{"DATE":"2017-02-11","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMTEgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"56":{"DATE":"2017-02-11","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMTEgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"57":{"DATE":"2017-02-12","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMTIgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"58":{"DATE":"2017-02-12","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMTIgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"59":{"DATE":"2017-02-12","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMTIgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"60":{"DATE":"2017-02-12","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMTIgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"61":{"DATE":"2017-02-13","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMTMgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"62":{"DATE":"2017-02-13","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMTMgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"63":{"DATE":"2017-02-13","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMTMgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"64":{"DATE":"2017-02-13","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMTMgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"65":{"DATE":"2017-02-13","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMTMgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"66":{"DATE":"2017-02-14","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMTQgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"67":{"DATE":"2017-02-14","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMTQgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"68":{"DATE":"2017-02-14","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMTQgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"69":{"DATE":"2017-02-14","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMTQgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"70":{"DATE":"2017-02-14","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMTQgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"71":{"DATE":"2017-02-15","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMTUgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"72":{"DATE":"2017-02-15","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMTUgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"73":{"DATE":"2017-02-15","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMTUgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"74":{"DATE":"2017-02-15","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMTUgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"75":{"DATE":"2017-02-15","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMTUgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"76":{"DATE":"2017-02-16","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMTYgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"77":{"DATE":"2017-02-16","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMTYgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"78":{"DATE":"2017-02-16","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMTYgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"79":{"DATE":"2017-02-16","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMTYgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"80":{"DATE":"2017-02-16","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMTYgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"81":{"DATE":"2017-02-17","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMTcgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"82":{"DATE":"2017-02-17","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMTcgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"83":{"DATE":"2017-02-17","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMTcgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"84":{"DATE":"2017-02-17","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMTcgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"85":{"DATE":"2017-02-17","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMTcgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"86":{"DATE":"2017-02-18","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMTggQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"87":{"DATE":"2017-02-18","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMTggQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"88":{"DATE":"2017-02-18","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMTggQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"89":{"DATE":"2017-02-18","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMTggQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"90":{"DATE":"2017-02-18","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMTggQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"91":{"DATE":"2017-02-19","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMTkgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"92":{"DATE":"2017-02-19","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMTkgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"93":{"DATE":"2017-02-19","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMTkgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"94":{"DATE":"2017-02-19","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMTkgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"95":{"DATE":"2017-02-19","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMTkgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"96":{"DATE":"2017-02-20","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMjAgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"97":{"DATE":"2017-02-20","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMjAgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"98":{"DATE":"2017-02-20","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMjAgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"99":{"DATE":"2017-02-20","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMjAgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"100":{"DATE":"2017-02-20","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMjAgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"101":{"DATE":"2017-02-21","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMjEgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"102":{"DATE":"2017-02-21","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMjEgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"103":{"DATE":"2017-02-21","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMjEgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"104":{"DATE":"2017-02-21","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMjEgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"105":{"DATE":"2017-02-21","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMjEgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"106":{"DATE":"2017-02-22","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMjIgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"107":{"DATE":"2017-02-22","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMjIgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"108":{"DATE":"2017-02-22","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMjIgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"109":{"DATE":"2017-02-22","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMjIgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"110":{"DATE":"2017-02-22","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMjIgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"111":{"DATE":"2017-02-23","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMjMgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"112":{"DATE":"2017-02-23","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMjMgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"113":{"DATE":"2017-02-23","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMjMgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"114":{"DATE":"2017-02-23","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMjMgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"115":{"DATE":"2017-02-23","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMjMgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"116":{"DATE":"2017-02-24","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMjQgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"117":{"DATE":"2017-02-24","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMjQgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"118":{"DATE":"2017-02-24","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMjQgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"119":{"DATE":"2017-02-24","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMjQgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"120":{"DATE":"2017-02-24","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMjQgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"121":{"DATE":"2017-02-25","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMjUgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"122":{"DATE":"2017-02-25","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMjUgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"123":{"DATE":"2017-02-25","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMjUgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"124":{"DATE":"2017-02-25","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMjUgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"125":{"DATE":"2017-02-25","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMjUgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"126":{"DATE":"2017-02-26","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMjYgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"127":{"DATE":"2017-02-26","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMjYgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"128":{"DATE":"2017-02-26","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMjYgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"129":{"DATE":"2017-02-26","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMjYgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"130":{"DATE":"2017-02-26","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMjYgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"131":{"DATE":"2017-02-27","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMjcgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"132":{"DATE":"2017-02-27","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMjcgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"133":{"DATE":"2017-02-27","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMjcgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"134":{"DATE":"2017-02-27","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMjcgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"135":{"DATE":"2017-02-27","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMjcgQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"},"136":{"DATE":"2017-02-28","TIME_RANGE":1,"PaX":"LS0tLTIwMTctMDItMjggQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMQ==","Availability":"true"},"137":{"DATE":"2017-02-28","TIME_RANGE":2,"PaX":"LS0tLTIwMTctMDItMjggQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMg==","Availability":"true"},"138":{"DATE":"2017-02-28","TIME_RANGE":3,"PaX":"LS0tLTIwMTctMDItMjggQU5EIHRpbWUgcmFuZ2UgaWQgaXMgMw==","Availability":"true"},"139":{"DATE":"2017-02-28","TIME_RANGE":4,"PaX":"LS0tLTIwMTctMDItMjggQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNA==","Availability":"true"},"140":{"DATE":"2017-02-28","TIME_RANGE":5,"PaX":"LS0tLTIwMTctMDItMjggQU5EIHRpbWUgcmFuZ2UgaWQgaXMgNQ==","Availability":"true"}}
```




# How To get STADIUM_ID ? 
The STADIUM_ID will provided by baratit .
for Testing purpose you can use these STADIUM_ID's

| STADIUM_ID     | STADIUM Name   |
| --------|---------|
| 33 |ملعب تجريبي  1|
| 34 |ملعب تجريبي  2|

# How To get BOOKING_TIME_RANGE_id ? 
The BOOKING_TIME_RANGE_id Could be change in the future ,
if there are any changes will be provided by baratit .

| BOOKING_TIME_RANGE_id     | Time range |
| --------|---------|
| 1 | من الساعة 4 مساءاً إلى 6 مساءاً|
| 2 | من الساعة 6 مساءاً إلى 8 مساءاً|
| 3 | من الساعة 8 مساءاً إلى 10 مساءاً|
| 4 | من الساعة 10 مساءاً إلى 12 صباحاً|
| 5 | من الساعة 12 صباحاً إلى 2 صباحاً|


# API Errors Reference
Some Times Somthing Just Gone Wrong and it is hard to Debug so Our System is smart enough,
to Repoert an Error Before excuteing any FUNCTION , and here it is a Reference for all Errors that you might face when start to integration with our system

| Error Numer     | Error Messge    | Explain |
| --------|---------|-------|
| 0001  | missing authentication DATA   | Check Your GET DATA in your Request the API_USER & API_PASS is missing or equal to zero |
| 0002  | not vaild authentication DATA   | Check Your GET DATA in your Request the API_USER & API_PASS is not vaild meaning they are wrong |
| 0011  | missing STADIUM_ID   | Check Your GET DATA in your Request the STADIUM_ID is missing or equal to zero |
| 0012  | missing BOOKING_DATE   | Check Your GET DATA in your Request the BOOKING_DATE is missing or equal to zero |
| 0013  | missing BOOKING_TIME_RANGE_id   | Check Your GET DATA in your Request the BOOKING_TIME_RANGE_id is missing or equal to zero |
| 0014  | missing USER_PHONE   | Check Your GET DATA in your Request the USER_PHONE is missing or equal to zero |
| 0015  | missing USER_NAME   | Check Your GET DATA in your Request the USER_NAME is missing or equal to zero |
| 0016  | BOOKING_DATE timestamp not vaild    | BOOKING_DATE must be as timestamp , the length must be equal to 12, unix timestamp Example : 1489352400000 -> 12/3/2016  |
| 0017  | BOOKING_TIME_RANGE_id not vaild   | BOOKING_TIME_RANGE_id must be from 1 to 5 only as INTEGR value |
| 0019  |  wrong STADIUM_ID not found   | STADIUM_ID that you provided in GET DATA is not vaild meaning wrong STADIUM_ID number  |
| 0018  |  This book is not ALLOWED   | that mean you can not make a book with this Date and time range because there are already booking with this Date an time range in this STADIUM_ID |
| 0020  | missing BOOKING_ID   | Check Your GET DATA in your Request the BOOKING_ID is missing or equal to zero |
| 0021  |  Alredy CANCELED book  | this booking is Alredy CANCELED  |



