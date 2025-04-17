# Hospital Management App – Calendar & Appointment Scheduling System

## Overview

This project is part of a larger **Hospital Management Application** developed by multiple teams. Our team was responsible for implementing the **calendar system** and **appointment management features** for patients.

The goal was to allow patients to view, interact with, and manage their upcoming appointments through a user-friendly and dynamic calendar interface.

## Features Implemented

### ✅ Calendar Integration
- **Interactive calendar** built with `CalendarView`, `CalendarEvent`, and C#.
- Appointments are displayed in calendar format for easy visualization.
- Dynamic updates using `ObservableCollection` ensure the calendar reflects real-time changes.

### ✅ Appointment Repository (Data Layer)
- `AppointmentRepository` handles all database interactions for appointments.
- Functions implemented:
  - `GetAllAppointments()` – retrieves all upcoming appointments for a patient.
  - `DeleteAppointment(appointmentId)` – removes an appointment if allowed.
- Fully respects the MVC pattern with proper database transaction handling.
- Repository is interface-based (`IAppointmentRepository`) for clean architecture.

### ✅ Appointment Service (Business Logic Layer)
- `AppointmentService` connects the UI to the repository and applies business rules.
- Functions implemented:
  - `GetAppointmentsForPatient(patientId)` – fetches future appointments for a specific patient.
  - `CancelAppointment(appointmentId)` – enforces the **24-hour cancellation rule**.
- Built with an `IAppointmentService` interface to protect logic from direct UI calls.
- Handles edge cases and exceptions (appointment not found, too late to cancel, etc.).

### ✅ Appointment Details Overlay
- When an appointment is clicked, a **modal overlay** (via `ContentDialog`) displays:
  - Date and time
  - Doctor name and department
  - Type of procedure
  - Location
- If cancellation is permitted (more than 24 hours in advance), a **Cancel button** appears.
- The cancel button is:
  - **Disabled and faded red** if less than 24 hours remain.
  - **Active and clickable** otherwise.

### ✅ Cancellation Functionality
- Patients can cancel appointments directly from the overlay.
- UI triggers `CancelAppointment(appointmentId)` from the service layer.
- Calendar updates in real time to reflect the cancellation.

## Architecture

Follows the **Model-Repository-Service-UI (MRSU)** pattern:

- **Model** – Appointment class and domain logic.
- **Repository** – Handles direct database interactions.
- **Service** – Contains all business logic.
- **UI** – XAML-based front-end using `CalendarView` and `ContentDialog`.

## Technologies Used

- C# and .NET
- XAML for UI
- MVVM/MVC architectural patterns
- `ObservableCollection` for reactive UI updates


## Final Result

The implementation allows patients to:
- **See their appointments at a glance**
- **Click on any appointment to view full details**
- **Cancel eligible appointments while respecting business rules**

This setup ensures a clean separation of concerns, scalability for future development, and a smooth user experience for hospital patients.

