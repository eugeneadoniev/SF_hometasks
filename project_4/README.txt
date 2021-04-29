Flights without losses. SQL queries and analysis

1. PROBLEM

You are an analyst at the regional branch of the airline in Anapa. You learn that the company is going through hard times every winter: not all flights from Anapa pay off in the "low season". At the same time, there are directions that could potentially be profitable, but the company does not have enough aircraft to launch them. And your first task in your new position will be to help you find the lowest-profit flights.
The regional leadership does not make decisions about canceling flights, but only transfers information about unprofitable flights to the central branch. However, the company has accumulated so much data that no one can pull the necessary information from the database. It is you who have to deal with the database and get the necessary data from it. And the conclusions will then have to be presented to senior management.
You have access to the database of all branches of the airline. It is necessary to provide such a table that will optimize the winter flights of Anapa.

2. PURPOSE OF THE PROJECT
Identify the least profitable winter flights from Anapa in 2017.
To achieve this goal, you must:
- form a SQL query to the database;
- based on the received dataset, determine the least profitable flights.

3. DIAGRAM DIAGRAM

The database is located in the tutorial Metabase and is named dst_project.
Database link: http://sql.skillfactory.ru:3000/

The main entity is the bookings table.
Several passengers can be included in one booking, each of whom is issued a separate ticket (tickets). The ticket has a unique number and contains information about the passenger. As such, the passenger is not a separate entity. Both the name and the number of the passenger's document can change over time, so that it is impossible to unambiguously find all the tickets of one person; for simplicity, we can assume that all passengers are unique.
The ticket includes one or more flights (ticket_flights). Several flights may be included in the ticket in cases where there is no direct flight connecting the points of departure and destination (flight with transfers), or when the ticket is taken “there and back”. There is no hard limit in the data schema, but it is assumed that all tickets in the same booking have the same set of flights.
Each flight (flights) goes from one airport (airports) to another. Flights with the same number have the same origin and destination, but will differ in departure date.
At check-in, the passenger is issued a boarding pass (boarding_passes), which indicates the seat on the plane. A passenger can only check-in for the flight that he has on the ticket. The combination of flight and seat must be unique to prevent the issuance of two boarding passes per seat.
The number of seats (seats) in the aircraft and their distribution by class of service depends on the model of the aircraft (aircrafts) performing the flight. It is assumed that each aircraft model has only one cabin layout. The data schema does not verify that boarding pass seats match those on the plane (this can be done using table triggers or in the app).

TABLE BOOKINGS.AIRCRAFTS
Each aircraft model is identified by its three-digit code (aircraft_code). The name of the model (model) and the maximum flight range in kilometers (range) are also indicated.

TABLE BOOKINGS.AIRPORTS
The airport is identified by a three-letter code (airport_code) and has its own name (airport_name).
There is no separate entity for the city, but the name (city) is indicated and can be used to identify the airports of one city. The latitude, longitude and timezone are also specified.

TABLE BOOKINGS.BOARDING_PASSES
When checking in for a flight, which is possible one day before the scheduled departure date, the passenger is issued a boarding pass. It is identified in the same way as the flight - by the ticket number and flight number.
Boarding passes are assigned sequential numbers (boarding_no) in the order in which passengers are checked in for the flight (this number will be unique only within the given flight). The boarding pass indicates the seat number (seat_no).

TABLE BOOKINGS.BOOKINGS
A passenger in advance (a maximum of a month before the flight) books a ticket for himself and, possibly, for several other passengers (booking date - book_date). The reservation is identified by a number (book_ref, a six-digit combination of letters and numbers).
The total_amount field stores the total cost of all passengers included in the booking.

TABLE BOOKINGS.FLIGHTS
The natural key of the flights table consists of two fields - the flight number (flight_no) and the departure date (scheduled_departure). To make foreign keys for this table more compact, a surrogate key (flight_id) is used as the primary key.
A flight always connects two points - the airports of departure (departure_airport) and arrival (arrival_airport). There is no such thing as a “connecting flight”: if there is no direct flight from one airport to another, the ticket pro