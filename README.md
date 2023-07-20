# About

A hotel company is looking for a way to predict whether or not a guest will cancel their booking

# Dataset

Source: [Hotel Booking Dataset](https://www.sciencedirect.com/science/article/pii/S2352340918315191#s0005)

## Data Dictionary
- `hotel`: Speficies if the hotel is a City Hotel or Resort Hotel
- `is_canceled`: Whether or not the booking was canceled
- `lead_time`: Number of days that elapsed between the entering date of the booking and the arrival date
- `arrival_date_year`: Year of arrival date
- `arrival_date_month`: Month of arrival date with 12 categories: “January” to “December”
- `arrival_date_week_number`: Week number of the arrival date
- `arrival_date_day_of_month`: Day of the month of the arrival date
- `stays_in_weekend_nights`: Number of weekend nights (Saturday or Sunday) the guest stayed or booked to stay at the hotel
- `stays_in_week_nights`: Number of week nights (Monday to Friday) the guest stayed or booked to stay at the hotel
- `adults`: Number of adults
- `children`: Number of children
- `babies`: Number of babies
- `meal`: Type of meal booked. Categories are presented in standard hospitality meal packages:
Undefined/SC – no meal package;
BB – Bed & Breakfast;
HB – Half board (breakfast and one other meal – usually dinner);
FB – Full board (breakfast, lunch and dinner)
- `country`: Country of origin. Categories are represented in the ISO 3155–3:2013 format
- `market_segment`: Market segment designation. In categories, the term “TA” means “Travel Agents” and “TO” means “Tour Operators”
- `distribution_channel`: Booking distribution channel. The term “TA” means “Travel Agents” and “TO” means “Tour Operators”
- `is_repeated_guest`: Value indicating if the booking name was from a repeated guest (1) or not (0)
- `previous_cancellations`: Number of previous bookings that were cancelled by the customer prior to the current booking
- `previous_bookings_not_canceled`: Number of previous bookings not cancelled by the customer prior to the current booking
- `reserved_room_type`: Code of room type reserved. Code is presented instead of designation for anonymity reasons
- `assigned_room_type`: Code of room type assigned. Code is presented instead of designation for anonymity reasons
- `booking_changes`: Number of changes/amendments made to the booking from the moment the booking was made until the moment of check-in or cancellation
- `deposit_type`: Indication on if the customer made a deposit to guarantee the booking. This variable can assume three categories:
No Deposit – no deposit was made;
Non Refund – a deposit was made in the value of the total stay cost;
Refundable – a deposit was made with a value under the total cost of stay.
- `agent`: ID of the travel agency that made the bookinga
- `company`: ID of the company/entity that made the booking or responsible for paying the booking. ID is presented instead of designation for anonymity reasons
- `days_in_waiting_list`: Number of days the booking was in the waiting list before it was confirmed to the customer
- `customer_type`: Type of booking, assuming one of four categories:
Contract - when the booking has an allotment or other type of contract associated to it;
Group – when the booking is associated to a group;
Transient – when the booking is not part of a group or contract, and is not associated to other transient booking;
Transient-party – when the booking is transient, but is associated to at least other transient booking
- `adr`: 	Average Daily Rate as defined by dividing the sum of all lodging transactions by the total number of staying nights
- `required_car_parking_spaces`: Number of car parking spaces required by the customer
- `total_of_special_requests`: Number of special requests made by the customer (e.g. twin bed or high floor)
- `reservation_status`: Reservation last status, assuming one of three categories:	
Canceled – booking was canceled by the customer;
Check-Out – customer has checked in but already departed;
No-Show – customer did not check-in and did inform the hotel of the reason why
- `reservation_status_date`: Date at which the last status was set. This variable can be used in conjunction with the ReservationStatus to understand when was the booking canceled or when did the customer checked-out of the hotel


# Findings
Check this [notebook](eda.ipynb) to see the EDA. According to the sample data:
- 37% of the bookings in the dataset were canceled.
- 47% of the clients would arrive in the year 2016, 34% in the year 2017 and 18% in the year 2015. There is an increase of bookings from 2015 to 2016 and a decrease from 2016 to 2017 because the dataset only has bookings that would arrive from 1st of July of 2015 and the 31st of August 2017. 
- January had the fewest number of bookings and it peaked around October. March to June had a consistent percentage of 9% with a drop in the month of July.
- There were fewer bookings in the first 6 weeks of the year 2016.
- Bookings were spread out through out the month but 31st day of the month had the fewest bookings. Maybe this is because are fewer months with 31 days
- 43% of the bookings had 0 number of weekend nights (Saturday or Sunday) the guest stayed or booked to stay at the hotel. Only 6% of guests did not book to stay in the hotel on weekday night. 53% of the guests booked 1-2 weekday nights.
- 40% of bookings were made in Portugal and looking at the top 10 countries, most of the guests are European.
- City hotel had more canceled bookings than bookings were the customer showed up.
- Guests who booked for 5-9 weekend nights are more likely to cancel their booking. While guests who booked 13-14 or 18-19 rarely canceled their bookings.
- Guests who booked for 12-24 week nights are more likely to cancel their booking. 
- Bookings that have more than 5 adults definetly cancel their bookings.
- Guests who booked full board meal packages are more likely to cancel their bookings.
- Repeated Guests are less likely to cancel their bookings. Guests who have canceled before atleast once, are more likely to cancel again. Guests who have previously canceled more than 11 times are also more likely to cancel again
- Guests who deposited the whole amount were more likely to cancel their bookings

# Modeling
Check out this [notebook](feature_engineering.ipynb) where I Feature Engineer and  build a RandomForestClassifier to predict whether or not a guest will cancel will cancel their booking