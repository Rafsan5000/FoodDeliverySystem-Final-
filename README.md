# Hotel Management System - C# WinForms + SQL Server LocalDB

This project is a multi-hotel management application converted from the original food-delivery project while keeping the existing UI/forms and C# structure.

## Database

- Server: `(localdb)\\MSSQLLocalDB`
- Database: `HotelManagementDB`
- Authentication: Windows Authentication
- Framework: .NET Framework 4.7.2
- Data access: `System.Data.SqlClient`
- Connection string is stored in `App.config` under `RestaurantDb`.

## Run the database

1. Open SQL Server Management Studio (SSMS).
2. Connect to `(localdb)\\MSSQLLocalDB`.
3. Open `Database_HotelManagementDB.sql`.
4. Execute the complete script.
5. In Object Explorer, refresh `Databases` and confirm `HotelManagementDB` exists.

The script creates:

- `Admin`
- `Customer`
- `Employee`
- `LogIn`
- `Hotels`
- `Rooms`
- `Bookings`
- `Food` (kept for the original food screens)
- `Orders` (kept for the original cart/order screens)
- `vw_BookingSummary`
- `vw_HotelDashboardStats`

## Sample login accounts

### Admin
- ID: `SA001`
- Password: `Admin@123`

### Employee
- ID: `EMP001`
- Password: `Employee@123`

### Customer
- ID: `CUS001`
- Password: `Customer@123`

Additional admin and employee accounts are included in the SQL seed data.

## Application flow

### Admin
`LogInForm -> Admin -> AdminLogIn -> AdminDashBoard`

Admin dashboard provides:

- Customer management
- Employee CRUD
- Hotel CRUD
- Room CRUD
- Booking management
- Super Admin account management for SuperAdmin users
- Dashboard statistics

### Employee
`LogInForm -> Employee -> EmployeeDashBoard`

Employee dashboard provides booking management and booking-status updates.

### Customer
`LogInForm -> Customer -> CustomerDashBoard`

Customer dashboard provides:

- Profile update
- Browse available hotel rooms
- Check-in/check-out date selection
- Guest count
- Booking confirmation
- Booking history
- Booking cancellation

## Hotel management

An admin can add, update and deactivate multiple hotels. Each hotel can contain multiple rooms.

Room fields:

- Room ID
- Hotel
- Room number
- Room type
- Capacity
- Price per night
- Description
- Status (`Available`, `Booked`, `Maintenance`)

## Booking rules

- Check-out must be after check-in.
- Guest count cannot exceed room capacity.
- A room cannot be booked when it is not available.
- Overlapping active bookings are rejected.
- Booking total = price per night × number of nights.
- Booking cancellation and employee status updates synchronize room availability.

## Visual Studio

If Visual Studio reports that `FoodDeliverySystem.exe` is missing, first fix the actual build error:

1. `Build -> Clean Solution`
2. Close Visual Studio.
3. Delete `bin` and `obj` folders.
4. Reopen the `.sln` file.
5. `Build -> Rebuild Solution`.
6. Confirm `bin\\Debug\\FoodDeliverySystem.exe` exists.
7. Press `F5`.

The missing EXE message is a result of a failed build; it is not a database connection error.
