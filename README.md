# Movie Ticket Booking Management Application
**National Internship Program (NIP) | Pega Platform™**

## Overview
CineWave Entertainment manages movie ticket bookings across multiple theatres and locations. This application, built on the Pega Platform™ as part of the National Internship Program (NIP), replaces manual email and offline tracking processes with a streamlined, automated workflow [cite: 1].

---

## Application Architecture & Case Lifecycle

The application is structured around a primary case type: **`Movie Ticket Request`** [cite: 1]. The end-to-end process is divided into distinct stages:

1. **Request Details Stage**
   - **US-001: Submit Movie Ticket Request**: Captures customer inputs including Movie Name, Show Date, Show Time, and Number of Tickets with validation for accuracy [cite: 1].
   - **US-005: Maintain Movie and Show Data**: Utilizes reusable **Movie** and **Show** data objects containing properties such as Genre and Seat Capacity to maintain consistency across requests [cite: 1].

2. **Availability & Pricing Stage**
   - **US-002: Check Show Availability**: Verifies seat availability status and available seat counts before allowing the booking to proceed [cite: 1].
   - **US-003: Calculate Booking Cost**: Automatically derives the `Total Cost` using a business rule based on `Ticket Price` and `Number of Tickets` [cite: 1].

3. **Approval Stage**
   - **US-004: Confirm Booking Request**: Assigned to the Customer persona to confirm or cancel the booking (`Booking Status`) [cite: 1].
   - **US-006: Review Booking Details**: Presents a structured summary interface displaying Movie Name, Show Timing, Number of Tickets, and Total Cost prior to confirmation [cite: 1].

4. **Booking Execution Stage**
   - **US-007: Process Ticket Booking**: Allocates seats, generates a unique `Ticket ID`, and updates the confirmation status [cite: 1].
   - **US-010: Route Booking Request by Show Type**: Automatically routes work items using a Decision Table or When rule to either **Premium ShowQueue** or **Standard ShowQueue** based on the show type [cite: 1].

---

## Service-Level Agreement (SLA) & Notifications

* **US-009: Define Booking SLA**: 
  - **Goal**: 1 day (flags the case as approaching deadline if missed) [cite: 1].
  - **Deadline**: 2 days (automatically increases case priority if missed) [cite: 1].
* **US-008: Notify Booking Confirmation**: Triggered upon case resolution, sending a correspondence email to the customer with booking particulars [cite: 1].

### Sample Correspondence (Email Body)
```text
Subject: Movie Ticket Booking Confirmed - [Case ID]

Dear [Customer Name],

Your movie ticket booking has been successfully confirmed.
Below are the details of your booking:
• Case ID: [Case ID]
• Movie Name: [Movie Name]
• Show Date & Time: [Show Date & Time]
• Number of Tickets: [Number of Tickets]
• Seat Numbers: [Seat Numbers]
• Total Cost: [Total Cost]

Please arrive at the theatre before show time and present your booking details at entry.

Thank you for choosing our services. Enjoy your movie!

Regards,
CineWave Entertainment - Booking Support Team
```

---

## Prerequisites & Getting Started
1. Complete the *Pega Environment Setup and Application Creation Guide* [cite: 1].
2. Use **Pega Blueprint** to generate the application scaffold [cite: 1].
3. Import or configure the user stories (US-001 through US-010) in your Academy instance [cite: 1].
