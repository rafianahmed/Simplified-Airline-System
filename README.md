# Airline Reservation System

## Overview

This is a **Python-based airline reservation system** that simulates flight bookings, cancellations, and ticketing. The system handles **multiple flights** and **transactions** while keeping track of seat availability for **First**, **Business**, and **Economy** classes.

It is designed to demonstrate:

* Python data structures (lists, dictionaries, tuples)
* Function-based modular programming
* String parsing and data manipulation
* Transaction processing logic (RES, CAN, TKT)

---

## Features

1. **Flight Parsing**

   * Reads flight information including flight number, date, time, origin, destination, seat availability, base fare, and miles.
   * Stores flights in a dictionary for fast access.

2. **Transaction Parsing**

   * Reads transaction data, including transaction ID, type (`RES`, `CAN`, `TKT`), member ID, flight, and seat booking info.
   * Processes each transaction in the order received.

3. **Reservation Management**

   * `RES` → Makes a reservation if enough seats are available.
   * `CAN` → Cancels a reservation if the member is authorized and the ticket is not issued.
   * `TKT` → Marks a reservation as ticketed; ticketed reservations cannot be canceled.

4. **Seat Counting**

   * The system can parse class codes such as `A-05J-10Y-20` to count seats for First (`A/F`), Business (`J/C`), and Economy (`Y/M/K`) classes.

5. **Output**

   * Prints any transaction errors (e.g., not enough seats, unauthorized cancel, ticketed cancel).
   * Displays the final reservation summary for each flight, including remaining seats.

---

## How It Works

1. **Data Input**

   * Sample flight and transaction data are stored as lists of strings.
   * Each flight record contains seat counts for First, Business, and Economy classes.
   * Each transaction specifies a type (reservation, cancel, ticket) and seat booking codes.

2. **Parsing**

   * `parse_flight_record(record, flights)` converts a flight record string into a Python dictionary.
   * `parse_transaction_record(record, transactions)` converts a transaction string into a Python dictionary.

3. **Processing Transactions**

   * `process_transaction(transaction, flights, reservations)` handles all transaction types:

     * **RES:** Checks seat availability and updates flight seats.
     * **CAN:** Restores seats and removes the reservation if allowed.
     * **TKT:** Marks reservation as ticketed.

4. **Counting Seats**

   * `count_seats(classcode)` reads the seat booking string and returns the number of seats booked per class as a tuple `(first, business, economy)`.

5. **Main Execution**

   * Reads all flight and transaction data.
   * Parses and processes transactions sequentially.
   * Prints errors for invalid or failed transactions.
   * Prints final reservations and available seats for each flight.

---

## Python Concepts Used

* **Data structures:** `dict` for flights and reservations, `list` for transactions, `tuple` for seat counts.
* **Functions:** Modular programming with reusable functions.
* **String manipulation:** `.split()`, `.replace()`, `.strip()`.
* **Control structures:** `for` loops, `if/elif/else` conditions.
* **Error handling:** Checks for seat availability, permission, and ticket status.

---

## Example Flight Record

```
AB123 2025-11-09 15:30 ICN JFK 10/20/50 500 10500.0
```

* Flight No: AB123
* Date: 2025-11-09
* Time: 15:30
* From: ICN, To: JFK
* Seats: 10 First / 20 Business / 50 Economy
* Base Fare: 500
* Miles: 10500.0

---

## Example Transaction Record

```
T0001 RES MB123 AB123 2025-11-09 15:30 A-05J-10Y-20
```

* Transaction ID: T0001
* Type: RES (Reservation)
* Member ID: MB123
* Flight No: AB123
* Date & Time: 2025-11-09 15:30
* Payload: A-05J-10Y-20 (5 First, 10 Business, 20 Economy seats requested)

---

## Output Example

```
T0003 - CANCEL ERROR: NO SUCH RESERVATION
Flight AB123202511091530: 0 reservations, [10, 20, 50] available
Flight CD456202511100900: 1 reservations, [3, 5, 20] available
```

---

## How to Run

1. Clone the repository.
2. Ensure you have Python 3 installed.
3. Run the main script:

```bash
python main.py
```

4. The system will print transaction errors and reservation summaries.

---


