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

# API documentation 

# (1) New Stadium Book 
this functions for make new book to particular Stadium at particular date and time-range .
* Required Parameter
```
- API_USER & API_PASS  // authentication DATA
- STADIUM_ID // the number ID of STADIUM that you want to make a book in
- BOOKING_DATE // the Date that you want to make a aboot at , must be as unix timestamp Example : 1489352400000 -> 12/3/2016
- BOOKING_TIME_RANGE_id
- USER_PHONE
- USER_NAME

```

* Request Example 






