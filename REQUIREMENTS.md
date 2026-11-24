# MedSync: Requirements

## Part A: User Stories

### Story 1: Patient books an appointment
As a patient, I want to book a free slot with a doctor,
so that I do not have to phone the clinic or wait in line to get a time.

Acceptance criteria:
- Given I am logged in as a patient, when I choose a doctor and a date, then I see only the slots that are still free.
- Given I select a free slot, when I confirm, then the appointment is saved and I see a confirmation with the doctor, date and time.
- Given the slot was booked by someone else a moment ago, when I confirm, then I see "Slot no longer available" and my booking is not created.
- Given I am not logged in, when I try to book, then I am sent to the login page and no booking is created.
- Given the doctor does not work on the chosen date, when I open that date, then I see "No slots available".

### Story 2: Double booking is prevented
(You write this one: story + at least 4 acceptance criteria, including one concurrency case.)

### Story 3: Live queue position
(You write this one: story + at least 4 acceptance criteria, including one unhappy path.)

## Part B: Non-Functional Requirements
1. Performance: the booking page loads in under 3 seconds on a typical 4G connection.
2. Security: passwords are hashed, and a patient can never read another patient's data.
3. Availability: the clinic can keep working during the day; planned downtime only outside clinic hours.
4. Mobile usability: every patient-facing page works on a 360px-wide phone screen.
5. Data privacy: only the minimum personal data is stored, and no personal data appears in logs.
