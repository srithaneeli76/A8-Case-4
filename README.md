# MIST4610 – GROUP PROJECT#1 – Case 4: Campus Club Fair📚

## Group Information: 

Group Name: A8 

Member Names: 
1. Sritha Neeli (Group Leader) 
2. Aman Bhavsar (SQL Writer) 
3. Dylan Foley (Database Designer) 
4. Luzmia Belman (Data Wrangler) 
5. Daniel Choi (Conceptual Modeler) 

## Case Description:

The objective of this case is to develop a relational database for the Campus Club Pair ( CCCP) at Peachtree State University (Georgia) to manage student organizations and campus engagements. The data model includes memberships, events, attendance, and club funding. The sole purpose of the database is to manage the student organizations in a centralized way, and the goal is to model the complex relationships accurately to help the Student Life Director understand campus engagement and its finances.

Core Entities:
 Student- Stores student information such as ID, contact details, and graduation year, and connects to clubs through memberships, event attendance, and leadership roles.
 Event- Stores each club-hosted event, including its title, schedule, and location, and serves as a central entity for tracking attendance and participation.
 Officer roles-A second many-to-many relationship where a club has multiple leadership positions and a single student is permitted to hold these roles in more than one club.
 Funding requests- The Funding Request entity is central here, linking to Club (the requester), Staff (the reviewer and optional backup reviewer), and Purchase (the actual expenditure).
 Fair/Table setup- For every fair, a club must reserve at least one table. This is created by an identifying many-to-many relationship between club and fair to create a new table titled reservation. A fair can host many clubs and a club can attend many fairs.
 Club- Stores information about each student organization, including its category, contact details, and formation date, and serves as the central entity for memberships, events, and funding activities.

Extension: At club events, certain clubs are able to bring guest speakers to come in and speak to their members. These guest speakers are employees of specific companies. For example, Google (the company) can have one of their Software Engineers (guest speakers) come in for a club event and talk about the company, their position, or whatever topic they choose to. The extension allows the model to track the speakers, the companies they represent, and the events they participate in.

## Data Model: 


<img width="974" height="705" alt="image" src="https://github.com/user-attachments/assets/879d054e-a8f2-4941-a7d3-bf72cd9ec584" />




Explanation: The data model is built around several entities that manage student organizations and their activities/roles. The student entity stores student information such as ID, contact details, and graduation year, and connects to clubs through memberships, event attendance, and leadership roles. The event entity stores each club-hosted event, including its title, schedule, and location, and serves as a central entity for tracking attendance and participation. The Funding Request entity is central here, linking to Club (the requester), Staff (the reviewer and optional backup reviewer), and Purchase (the actual expenditure). The club entity stores information about each student organization, including its category, contact details, and formation date, and serves as the central entity for memberships, events, and funding activities. The Officer role is a second many-to-many relationship in which a club has multiple leadership positions, and a single student may hold these roles in more than one club. Lastly, for every fair, a club must reserve at least one table. This is created by identifying a many-to-many relationship between club and fair to create a new table titled reservation. A fair can host many clubs, and a club can attend many fairs. The Membership entity is used to store "Join Date" and "Status," which are attributes of the relationship rather than the student or club alone. The event host entity is a critical associative entity between the Club and Event. It resolves the M: M relationship and includes a boolean or attribute for "Primary Host" vs. "Partner Host." Lastly, the attendance entity captures transaction-specific data: whether the student was checked in and the specific service hours earned for that specific event.

Entity relationships: (Asks explanation to be about the relationships, not individual entities)
Membership- We use this to store "Join Date" and "Status," which are attributes of the relationship rather than the student or club alone. A student can enroll in many clubs and each club has many students.
Event_Host- This is a critical many-to-many relationship between Club and Event. It includes an attribute for "Primary Host" vs. "Partner Host". A club can host many events and an event can be co-hosted by multiple clubs. 
Attendance- This captures transaction-specific data: whether the student was checked in and the specific service hours earned for that specific event. A student attends many events and each event has many student attendees.
Reservation: This is a many-to-many relationship between club and fair. This shows that a club can attend many different fairs and a fair hosts many different clubs. In other words, it shows that a club can only request one reservation per fair, with a club hosting many reservations.
Staff: Between the staff to funding request entities, we have two one to many relationships representing the primary staff and secondary staff. Both are nonidentifying, but the secondary reviewer has an optional modality as it can be null. 
Sister Clubs: This is handled via a Recursive (Self-Referencing) Relationship on the Club table, where a SisterClubID foreign key points back to another ClubID, restricted to a 1:1 mapping
 

## Data Dictionary:

<img width="791" height="489" alt="Screenshot 2026-04-08 at 3 35 03 PM" src="https://github.com/user-attachments/assets/58dc340a-56b2-4b7f-acf5-9984e0663c1d" />
<img width="790" height="413" alt="Screenshot 2026-04-08 at 3 36 04 PM" src="https://github.com/user-attachments/assets/216ea8de-d1f1-426c-a795-f6ac616be3f4" />
<img width="789" height="444" alt="Screenshot 2026-04-08 at 3 36 52 PM" src="https://github.com/user-attachments/assets/d3957f0a-507b-4e63-b7b6-eb883980dded" />
<img width="792" height="539" alt="Screenshot 2026-04-08 at 3 37 24 PM" src="https://github.com/user-attachments/assets/39ea4dd3-6c69-4e78-880a-86f3e0c1bfad" />
<img width="788" height="451" alt="Screenshot 2026-04-08 at 3 37 38 PM" src="https://github.com/user-attachments/assets/a54c1b7c-1b50-49c0-8beb-ec19e5bbd843" />
<img width="790" height="489" alt="Screenshot 2026-04-08 at 3 37 49 PM" src="https://github.com/user-attachments/assets/ef3f68ef-2cca-40de-b52b-1df9b3d63c02" />
<img width="790" height="345" alt="Screenshot 2026-04-08 at 3 38 03 PM" src="https://github.com/user-attachments/assets/650fc972-7f1f-4d35-815b-991c874a307d" />
<img width="788" height="512" alt="Screenshot 2026-04-08 at 3 38 17 PM" src="https://github.com/user-attachments/assets/ff7b6dfc-0064-48ab-a424-1f0749d65f38" />
<img width="785" height="461" alt="Screenshot 2026-04-08 at 3 38 31 PM" src="https://github.com/user-attachments/assets/0842de1d-0af8-4408-8193-b13edf41b799" />
<img width="786" height="506" alt="Screenshot 2026-04-08 at 3 38 44 PM" src="https://github.com/user-attachments/assets/021f5b14-d43e-44e9-b1a3-1c9909e84db8" />
<img width="786" height="548" alt="Screenshot 2026-04-08 at 3 38 57 PM" src="https://github.com/user-attachments/assets/4de78686-9ba7-4754-9c1b-1d30033e84fd" />

## Queries:
### Simple Query #1: Which students are currently active members of a club?

Managerial Justification: 
This helps club officers and event planners quickly identify currently active student members for communication, recruitment, and participation tracking.

Code:
```SQL
SELECT DISTINCT s.student_f_nm,
                s.student_l_nm
FROM student s
JOIN membership m
  ON s.student_id = m.student_id
WHERE LOWER(m.member_status) = 'active'
ORDER BY s.student_l_nm, s.student_f_nm;
```
Query Results:

<img width="165" height="169" alt="Screenshot 2026-04-09 at 5 45 54 PM" src="https://github.com/user-attachments/assets/79504e70-87e1-44f3-80b8-c43da810a06c" />

### Simple Query #2: What upcoming events are scheduled and in what order will they occur?

Managerial Justification: 
This helps staff and student leaders stay organized, promote future events, and prepare logistics in chronological order.

Code:
```SQL
SELECT event_title,
       event_date,
       event_start_time,
       event_end_time,
       event_location
FROM events
WHERE event_date >= CURDATE()
ORDER BY event_date ASC, event_start_time ASC;
```
Query Results:

<img width="563" height="258" alt="Screenshot 2026-04-08 at 4 41 02 PM" src="https://github.com/user-attachments/assets/c8fa9046-5d05-4975-a972-2e17d4cc8341" />

### Simple Query #3: Which students have joined a club and when did they join?

Managerial Justification: This helps managers and club leaders track membership growth over time and identify recently joined students for onboarding or outreach.

Code:
```SQL
SELECT s.student_f_nm,
       s.student_l_nm,
       s.student_email,
       m.join_date
FROM student s
JOIN membership m
  ON s.student_id = m.student_id
ORDER BY m.join_date DESC;
```
Query Results:

<img width="337" height="151" alt="Screenshot 2026-04-08 at 4 42 36 PM" src="https://github.com/user-attachments/assets/440730de-667e-4699-87a9-63b656a4f5d9" />

### Simple Query #4: Which fair reservations require power access and for which fair were they made?

Managerial Justification: This helps event organizers prepare table layouts and electrical setup ahead of time for each club fair.

Code:
```SQL
SELECT r.table_id,
       r.power_access_request,
       f.fair_date,
       f.fair_venue
FROM reservation r
JOIN fair f
  ON r.fair_fair_id = f.fair_id
ORDER BY f.fair_date, r.table_id;
```

Query Results:

<img width="391" height="156" alt="Screenshot 2026-04-08 at 5 43 14 PM" src="https://github.com/user-attachments/assets/e30cc617-ef7e-4408-aba0-5e34663a3de4" />


### Complex Query #5: Which students have never attended any recorded event?

Managerial Justification: This helps administrators identify students who may be less engaged and may benefit from targeted outreach or involvement opportunities.

Code:
```SQL
SELECT s.student_id,
       s.student_f_nm,
       s.student_l_nm,
       s.student_email
FROM student s
WHERE s.student_id NOT IN (
    SELECT ar.student_id
    FROM attendance_records ar
    WHERE LOWER(ar.attendance_checked) = 'yes')
ORDER BY s.student_l_nm, s.student_f_nm;
```
Query Results:

<img width="339" height="44" alt="Screenshot 2026-04-08 at 4 47 25 PM" src="https://github.com/user-attachments/assets/299b9283-f8dd-4495-af42-ccffbe396543" />

### Complex Query #6: Which clubs currently have the highest number of active members?

Managerial Justification: This helps campus leadership identify highly engaged clubs and allocate space, resources, or promotional support more effectively.

Code:
```SQL
SELECT c.club_name,
       COUNT(s.student_id) AS active_member_count
FROM club c
JOIN membership m
  ON c.club_id = m.club_id
JOIN student s
  ON s.student_id = m.student_id
WHERE LOWER(m.member_status) = 'active'
GROUP BY c.club_id, c.club_name
ORDER BY active_member_count DESC, c.club_name;
```
Query Results:

<img width="352" height="125" alt="Screenshot 2026-04-09 at 5 11 10 PM" src="https://github.com/user-attachments/assets/9ee77794-8b9b-4a7c-b4d7-d0e7cedb2b32" />

### Complex Query #7: Which events had the highest student attendance?

Managerial Justification: This helps event planners evaluate which events were most successful and use that information when planning future programming.

Code:
```SQL
SELECT e.event_title,
       e.event_date,
       COUNT(*) AS attendees_count
FROM attendance_records ar
JOIN events e
  ON e.event_id = ar.event_id
WHERE LOWER(ar.attendance_checked) = 'yes'
GROUP BY e.event_id, e.event_title, e.event_date
ORDER BY attendees_count DESC, e.event_date;
```
Query Results:

<img width="321" height="138" alt="Screenshot 2026-04-09 at 5 14 28 PM" src="https://github.com/user-attachments/assets/6b229c4c-0b51-4708-9d9c-0e4bce5eadb2" />

### Complex Query #8: Which club fairs had the highest number of club reservations?

Managerial Justification: This helps organizers understand which fairs generated the most interest and can guide planning for venue size, staffing, and table availability.

Code:
```SQL
SELECT f.fair_date,
       f.fair_venue,
       COUNT(DISTINCT c.club_id) AS clubs_reserved
FROM fair f
JOIN reservation r
  ON f.fair_id = r.fair_fair_id
JOIN club c
  ON c.club_id = r.club_club_id
GROUP BY f.fair_id, f.fair_date, f.fair_venue
HAVING COUNT(DISTINCT c.club_id) > 1
ORDER BY clubs_reserved DESC, f.fair_date;
```
Query Results:

<img width="254" height="45" alt="Screenshot 2026-04-08 at 5 24 25 PM" src="https://github.com/user-attachments/assets/405b4c55-d70a-4e0e-9109-67e48907940c" />

### Complex Query #9: Which guest speakers have participated in more than one event?

Managerial Justification: This helps organizers identify the most active clubs in event programming and better understand which clubs are contributing the most to campus engagement.

Code:
```SQL
SELECT c.club_id,
       c.club_name,
       COUNT(e.event_id) AS total_events
FROM club c
JOIN events e
  ON c.club_id = e.club_id
JOIN staff s
  ON e.staff_id = s.staff_id
GROUP BY c.club_id, c.club_name
HAVING COUNT(e.event_id) > 1
ORDER BY total_events DESC, c.club_name;
```
Query Results:

<img width="227" height="60" alt="Screenshot 2026-04-09 at 5 31 53 PM" src="https://github.com/user-attachments/assets/0d1cdebd-2898-421a-9012-e43e4c069314" />

### Complex Query #10: Which students are active members in more than one club?

Managerial Justification: This helps identify highly involved students who may be strong candidates for leadership, ambassador roles, or cross-club collaboration opportunities.

Code:
```SQL
SELECT s.student_id,
       s.student_f_nm,
       s.student_l_nm,
       COUNT(DISTINCT c.club_id) AS active_clubs
FROM student s
JOIN membership m
  ON s.student_id = m.student_id
JOIN club c
  ON c.club_id = m.club_id
WHERE LOWER(m.member_status) = 'active'
GROUP BY s.student_id, s.student_f_nm, s.student_l_nm
HAVING COUNT(DISTINCT c.club_id) > 1
ORDER BY active_clubs DESC, s.student_l_nm;
```
Query Results:

<img width="314" height="125" alt="Screenshot 2026-04-09 at 5 37 40 PM" src="https://github.com/user-attachments/assets/c3cf9c03-546e-46f2-9cb7-88c094866afd" />


### Feature Matrix
<img width="783" height="336" alt="Screenshot 2026-04-08 at 6 22 27 PM" src="https://github.com/user-attachments/assets/74fd99fe-9a16-4240-8cb3-712b5a02d770" />


## Database Information
Database Name: mb_A8

