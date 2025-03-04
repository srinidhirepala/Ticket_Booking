# Ticket Booking System (C Language)

## Overview
This project is a simple *Ticket Booking System* implemented in *C*. It allows users to:
- View available movies and their seat availability.
- Book tickets in real-time.
- Manage seat allocation dynamically.

## Features
- Displays a list of available movies with real-time seat availability.
- Allows users to book tickets based on availability.
- Ensures a smooth user experience with menu-driven navigation.

## Technologies Used
- *Programming Language*: C
- *Concepts Used*: Arrays, Structures, Loops, Functions, Conditional Statements

## How to Run
1. *Compile the code* using a C compiler bash (GCC, Turbo C, or any other compatible compiler).
   ```bash
   gcc ticket_booking.c -o ticket_booking
   ```
   
2. *Run the executable*:
   ```bash
   ./ticket_booking
   ```
   
3. Follow the on-screen instructions to book tickets.

Example Output

======================================
    WELCOME TO MOVIE BOOKING
======================================

Ticket Booking System
1. Book Ticket
2. Cancel Ticket
3. View Bookings
4. View Available Seats
5. Exit
Enter choice: 1

Available Movies:
1. Avengers: Endgame
2. Inception
3. The Dark Knight
4. Interstellar
Select Movie (1-4): 2

Available Timings:
1. 10:00 AM
2. 1:00 PM
3. 4:00 PM
4. 7:00 PM
Select Timing (1-4): 3

Available Seats: 1 2 3 4 5 6 7 8 9 10
Select Seat Number: 5

===================================
        BOOKING RECEIPT
===================================
Ticket ID   : 1
Movie       : Inception
Timing      : 4:00 PM
Seat Number : 5
===================================
Please check your receipt before leaving!!!

## Future Enhancements
To make this project more advanced, consider adding:
- *User authentication* (Login/Signup feature)
- *File handling* to save and retrieve booking data
- *Graphical User Interface (GUI)* using libraries like GTK or Ncurses
- *Multithreading* to handle concurrent bookings

## License
This project is open-source. You are free to modify and distribute it.
