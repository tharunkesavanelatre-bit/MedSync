# MedSync: Appointments & Live Queue for Clinics

## 1. Problem Statement

Small and mid-sized clinics still run on phone calls, paper registers and shouted names. Patients call to book and often cannot get through, then arrive not knowing how long they will wait. A patient with a 10:00 slot may be seen at 11:15 with no explanation. Receptionists spend the day on the phone and rewriting the schedule by hand when a doctor runs late or a patient does not show up. Doctors lose consultation time to no-shows and idle gaps, so patients lose hours, staff carry avoidable stress, and the clinic loses income.

## 2. Personas

### Priya, 29, patient (office worker)
- Goal: see the doctor close to her booked time and get back to work
- Frustration: the phone line is always busy, and she waits 1+ hour with no idea when her turn is
- Usage: books a slot online, checks her queue position, and arrives when it is nearly her turn

### Meena, 35, receptionist
- Goal: keep the day running smoothly and every patient in the right order
- Frustration: she is on the phone all day and rewrites the schedule by hand when the doctor runs late
- Usage: registers walk-ins, checks patients in, and sees the whole queue on one screen

### Dr. Arjun, 45, general physician
- Goal: see as many patients as possible without rushing consultations
- Frustration: no-shows leave idle gaps, and he does not know who is waiting outside
- Usage: sees the next patient on his screen and marks each consultation complete

## 3. MVP Scope

Decisions:
- Appointments and walk-ins share one queue, because that is how real clinics work.
- One clinic with multiple doctors. Multi-clinic support is later, but the database will be designed so it can be added.

Features (must have):
1. Register and log in, with roles: patient, receptionist, doctor, admin
2. Admin manages doctors and their working hours
3. Patient views available slots and books an appointment
4. Patient cancels or reschedules an appointment
5. Double booking of the same slot is prevented
6. Receptionist registers walk-in patients
7. Receptionist checks in arriving patients
8. Live queue: patients see their position, staff see the full queue (real-time)
9. Doctor calls the next patient and marks consultation complete
10. Appointment history for patients and daily list for staff

## 4. Out of Scope (for now)
- Online payments and billing: adds payment gateway and legal complexity
- Electronic health records and prescriptions: heavy medical and compliance requirements
- SMS / WhatsApp reminders: needs paid third-party services; email only later
- Video consultations: separate real-time media problem
- Insurance claims: needs integrations with outside systems
- Multi-clinic platform: tenant isolation is a big step, planned for v2
- Mobile app: the web app will be responsive instead

## 5. Success Criteria
1. A patient can book an available slot in under 60 seconds.
2. A queue change (check-in, call next) appears on all connected screens within 2 seconds.
3. When two users try to book the same slot at the same time, exactly one succeeds. Verified by an automated test.

## 6. Risks
1. Double booking from concurrent requests. Mitigation: database unique constraint plus transactions, tested with a concurrency test.
2. Real-time updates are new to me and could take long. Mitigation: build a basic version first with polling, then upgrade to WebSockets.
3. Scope creep. Mitigation: anything not in the MVP list goes into a backlog, not into the code.

## 7. Data Sensitivity
- Stored: name, phone, email, appointment history. No medical records in the MVP.
- Passwords are hashed, never stored as plain text.
- Role-based access: patients see only their own data; staff see only what their role needs.
- HTTPS in production, and no personal data in logs.
