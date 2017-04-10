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

# How To get STADIUM_ID ? 
The STADIUM_ID will provided by baratit .
for Testing purpose you can use these STADIUM_ID's

| STADIUM_ID     | STADIUM Name   |
| --------|---------|
| 33 |ملعب تجريبي  1|
| 34 |ملعب تجريبي  2|

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



