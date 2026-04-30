classDiagram
    class Customer {
        -String residentId
        -String password
        -String name
        -int mileage
        +register()
        +search()
        +authenticate() bool
        +getMileage() int
    }

    class Ticket {
        -String flightId
        -String seat
        -String departureTime
        -String arrivalTime
        -int price
        +register()
        +search()
        +getPrice() int
    }

    class Reservation {
        -String reservationId
        -String residentId
        -String flightId
        -String seat
        -String reservationDate
        -boolean isPurchased
        -int purchaseCost
        +createReservation(residentId, flightId, seat, date)
        +getReservation(reservationId) Reservation
        +processPurchase(mileage)
    }

    class ReservationSystem {
        <<Service>>
        +reserveTicket()
        +purchaseTicket()
        -generateReservationId(resId, flightId, seat) String
    }

    Customer "1" -- "0..5" Reservation : makes
    Ticket "1" -- "0..*" Reservation : reserved_as
    ReservationSystem ..> Customer : uses
    ReservationSystem ..> Ticket : uses
    ReservationSystem ..> Reservation : manages