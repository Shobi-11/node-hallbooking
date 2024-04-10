Hall Booking API Documentation

Introduction
Welcome to the Hall Booking API documentation. This API allows you to manage rooms, 
make bookings, and retrieve information about rooms and bookings.

Base URL `http://localhost:3000`
--------------------------------------------------------------------------------------------------------
Endpoints

Create a Room
- Endpoint: `/createRoom`
- Method: `POST http://localhost:3000/createRoom`
- Description: Create a new room with the specified number of seats, amenities, and price per hour.
- Request Body -> raw -> JSON
  {
    "seats": 50,
    "amenities": ["Projector", "Whiteboard"],
    "pricePerHour": 100
  }

- Response:
  {
    "id": 1,
    "seats": 50,
    "amenities": ["Projector", "Whiteboard"],
    "pricePerHour": 100
  }
--------------------------------------------------------------------------------------------------------  

Book a Room
- Endpoint: `/bookRoom`
- Method: `POST http://localhost:3000/bookRoom`
- Description: Book a room for a customer with the specified details.
- Request Body -> raw -> JSON
  {
    "customerName": "John Doe",
    "date": "2023-12-01",
    "startTime": "10:00 AM",
    "endTime": "12:00 PM",
    "roomId": 1
  }
  ```
- Response:
  {
    "id": 1,
    "customerName": "John Doe",
    "date": "2023-12-01",
    "startTime": "10:00 AM",
    "endTime": "12:00 PM",
    "roomId": 1
  }
--------------------------------------------------------------------------------------------------------

List all Rooms with Booked Data
- Endpoint: `/listRooms`
- Method: `GET`
- Description: Retrieve a list of all rooms with their booked status and booking details.
- Response:
  [
    {
      "roomName": "Room 1",
      "bookedStatus": true,
      "bookings": [
        {
          "id": 1,
          "customerName": "John Doe",
          "date": "2023-12-01",
          "startTime": "10:00 AM",
          "endTime": "12:00 PM"
        }
      ]
    }
  ]
--------------------------------------------------------------------------------------------------------  

List all Customers with Booked Data
- Endpoint: `/listCustomers`
- Method: `GET`
- Description: Retrieve a list of all customers with their booked room and booking details.
- Response:
  [
    {
      "customerName": "John Doe",
      "roomName": "Room 1",
      "date": "2023-12-01",
      "requested": "2023-11-18T12:00:00Z",
      "startTime": "10:00 AM",
      "endTime": "12:00 PM"
    }
  ]
--------------------------------------------------------------------------------------------------------  

List Customer Booking History
- Endpoint: `/customerBookingHistory/{customerName}`
- Method: `GET`
- Description: Retrieve the booking history for a specific customer.
- Response:
  [
    {
      "customerName": "John Doe",
      "roomName": "Room 1",
      "date": "2023-12-01",
      "startTime": "10:00 AM",
      "endTime": "12:00 PM",
      "bookingId": 1,
      "bookingDate": "2023-11-18T12:00:00Z",
      "bookingStatus": "Booked"
    }
  ]
------------------------------------------------------------------------------------------------------------------
Error Handling:-

In case of an error, the response will include an error message and an appropriate HTTP status code.

Note:-

Make sure to handle overlapping bookings to prevent double bookings for the same room, date, and time.
------------------------------------------------------------------------------------------------------------------
                                Can use local variables to store data
------------------------------------------------------------------------------------------------------------------
when a new room is created:-

const room = {
  id: rooms.length + 1,
  seats,
  amenities,
  pricePerHour,
};
rooms.push(room);
------------------------------------------------------------------------------------------------------------------
when a room is booked:-

const booking = {
  id: bookings.length + 1,
  customerName,
  date,
  startTime,
  endTime,
  roomId,
};
bookings.push(booking);
------------------------------------------------------------------------------------------------------------------