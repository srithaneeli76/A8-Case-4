# A8-Case-4
Group Information: 
Group Name:  A8 
Member Names: Sritha Neeli (Group Leader), Aman Bhavsar (SQL Write), Dylan Foley ( Database Designer), Luzmia Belman-Serrano (Data Wrangler), Daniel Choi (Conceptual Modeler) 

The objective of this case is to develop a relational database for the Campus Club Pair ( CCCP) at Peachtree State University (Georgia) to manage student organizations and campus engagements. The data model includes memberships, events, attendance, and club funding. The sole purpose of the database is to manage the student organizations in a centralized way, and the goal is to model the complex relationships accurately to help the Student Life Director understand campus engagement and its finances.
Extension: ( NEED TO ADD)

Data Model (NEED TO ADD)

DATA DICTIONARY (NEED TO ADD)

10 Queries 
1. Simple Query 1 — List all active club members with their full name and club
   SELECT student.student_f_nm, student.student_l_nm, club.club_name, membership.member_status 
FROM student, membership, club 
WHERE student.student_id = membership.student_id 
AND membership.club_id = club.club_id 
AND membership.member_status = 'active' ORDER BY student.student_l_nm;

