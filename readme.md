Thoriq Fadhilah A
---
## User Service (user dan admin)

Entity: user

- id
- username
- password
- email
- pw
- first name
- last name
- birth of date
- adress
- gender
- picture
- join date
- update date
- role

Insfrastruktur: UserRepository

Application layer: 

- Regis
    - id (increment)
    - username
    - password
    - email
    - pw
    - first name
    - last name
    - birth of date
    - adress
    - gender
- login
    - username
    - password
- update profil
    - picture(disable sementara)
    - first name
    - last name
    - birth of date
    - adress
    - gender
    - change password

Regis: User registrasi

Login: User/admin dapat login

Update Profile: User/Admin mengupdate profil


Alur Untuk User : User melakukan registrasi terlebih dahulu setelah berhasil melakukan regis user sign in, user berada pada halaman pertama lalu ke halaman profil, user dapat melakukan update profil

Alur untuk Admin: admin tidak perlu melakukan registrasi, langsung masuk ke login, dan admin juga dapat melakukan update profil


## Event Service (admin/user)

Insfrastruktur :EventRepository

Entity: Event

- id
- name_event
- price
- picture
- isAvailable
- stock
- created_date
- update_date
- isDelete

Application layer: 

- Create event
    - id (increment)
    - name_event
    - price
    - picture
    - isAvailable
    - stock
- update event
    - id
    - name_event
    - price
    - picture
    - stock
    - isAvailable
- delete event
    - id
    - name_event
- get event
    - name_event
- get event detail
    - name_event
    - stock
    - isAvailable

Alur Untuk User (Pre con: sudah auth): User dapat melihat event yang tersedia, dan user bisa masuk ke detail dari event tersebut

Alur untuk Admin(pre con: sudah login): Admin dapat membuat event terbaru atau mengedit dan menghapus event yang sudah ada ketika ada perubahan

## Booking Service(user)

Insfrastruktur: BookingRepository

Event: Booking

- id
- id_event (Foreign Key)
- id_user (Foreign Key)
- create_date
- end_date
- status_booking
- isExpired

Application layer: 

- Create booking (user)
    - id_event
    - id_user
    - status_booking
- cancel booking (user)
    - id_event
    - id_user
    - status_booking

Alur untuk User : User dapat membuat booking event dari event yang sudah dibuat tadi, dan user dapat cancel booking

## payment Service(user)

Insfrastruktur: PaymentRepository

Entity: payment

- id
- id_booking(Foreign Key)
- payment_method
    - transfer
    - qris
- status
- created_date

Application layer: 

- Create payment (user)
    - id
    - payment_method
    - status
- Update payment (user)
    - id
    - payment_method
    - status

Alur untuk User : User membuat pembayaran dari event yang sudah di booking tadi, setelah itu status akan berubah dan user dapat melakukan update pembayaran atau melakukan pembayaran itu sendiri

Teknologi dari setiap service yang akan digunakan

Nest JS: UserService, dan EventService

Golang: BookingService dan Payment Service

pemilihan teknologi disebabkan karena beberapa alasan

1. Service yang memiliki kinerja tinggi dan latency rendah menggunakan Golang
2. Jika service memiliki banyak request API disarankan menggunakan NestJs

## Diagram
Saga Pattern
![Alt text]( https://github.com/thoriq1520/oppty-edot/blob/main/Img/saga.png?raw=true "Saga")


Hexagonal Layerd
![Alt text](https://github.com/thoriq1520/oppty-edot/blob/main/Img/Hexagonal.png?raw=true "Hexagonal Layerd")

Hexagonal Diagram
![Alt text](https://github.com/thoriq1520/oppty-edot/blob/main/Img/hexa.png?raw=true "Hexagonal Diagram")
