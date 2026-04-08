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

Extension: (NEED TO ADD)

## Data Model: 

<img width="1509" height="1184" alt="MB_A8 DATA MODEL" src="https://github.com/user-attachments/assets/37b954c7-6e48-4899-a705-2b4a0cebf7d4" />

Explanation: (NEED TO ADD)

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

## Ten Queries:
### Simple Query #1: Which students are currently active members of a club?

Managerial Justification: 

Code:
```SQL
SELECT s.student_f_nm,
       s.student_l_nm
FROM student s
JOIN membership m
  ON s.student_id = m.student_id
WHERE LOWER(m.member_status) = 'active'
ORDER BY s.student_l_nm, s.student_f_nm;
```
Query Results:

<img width="201" height="123" alt="Screenshot 2026-04-08 at 4 31 48 PM" src="https://github.com/user-attachments/assets/a2b189d1-bcf9-4923-aaca-1517f34e30ac" />

### Simple Query #2: What upcoming events are scheduled and in what order will they occur?

Managerial Justification: 

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

### Simple Query #3: Which students have joined a club, and when did they join?

Managerial Justification: 

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

Managerial Justification: 

Code:

Query Results:

### Complex Query #5: Which students have never attended any recorded event?

Managerial Justification: 

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

Managerial Justification: 

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

<img width="350" height="121" alt="Screenshot 2026-04-08 at 4 49 12 PM" src="https://github.com/user-attachments/assets/07714f88-8709-47dd-a31a-61a15f9f6899" />

## Database Information

