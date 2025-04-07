Here's a complete **README** you can use for your GitHub repo:

---

# 🕵️ SQL Murder Mystery — Solved!

Welcome to my investigation of the **SQL Murder Mystery**, an interactive detective-style challenge that tests your SQL querying, logical thinking, and problem-solving skills — all through a data-driven crime case!

## 🧩 The Challenge

The task begins with a murder that took place in **SQL City**. You're given minimal initial clues and must use SQL queries to dig through city records, interview transcripts, vehicle and gym databases to track down:

- 🧍 The **murderer**  
- 🧠 The **mastermind behind the crime**

🔗 [Play the challenge here](https://mystery.knightlab.com/)

---

## 🛠️ Tools & Skills Used

- SQL querying (SELECT, JOIN, WHERE, INTERSECT, LIKE, ORDER BY)
- Pattern recognition
- Deductive logic
- Data analysis
- Investigative thinking

---

## 🕵️ Step-by-Step Case Breakdown

### 1. Investigated the Crime Scene
```sql
SELECT * 
FROM crime_scene_report 
WHERE type = 'murder' AND city = 'SQL City';
```
🗣️ Found there were **two witnesses** mentioned:
- One lives on **Northwestern Dr**
- One named **Annabel** on **Franklin Ave**

---

### 2. Identified the Witnesses
```sql
SELECT * 
FROM person 
WHERE address_street_name = 'Franklin Ave';
```
Found **Annabel Miller**, interviewed her:
```sql
SELECT * 
FROM interview 
WHERE person_id = 16371;
```
👀 She recognized the killer from her **gym**.

---

### 3. Found the Second Witness
Located the last house on Northwestern Dr:
```sql
SELECT * 
FROM person 
WHERE address_street_name = 'Northwestern Dr' 
ORDER BY address_number DESC;
```
Interviewed them:
```sql
SELECT * 
FROM interview 
WHERE person_id = 14887;
```
👜 They saw the killer with a **"Get Fit Now Gym"** bag (gold member), and a car with plate **containing H42W**.

---

### 4. Narrowed Down Gym Members
```sql
SELECT * 
FROM get_fit_now_member 
WHERE id LIKE '48Z%' AND membership_status = 'gold';
```
Found two suspects:  
- **Joe Germuska**  
- **Jeremy Bowers**

Checked who was at the gym on Jan 9:
```sql
SELECT * 
FROM get_fit_now_check_in 
WHERE membership_id = '48Z55' AND check_in_date = '20180109';
```
🕒 Jeremy Bowers was at the gym on the murder day.

Confirmed his license plate:
```sql
SELECT * 
FROM drivers_license 
WHERE id = 423327 AND plate_number LIKE '%H42W%';
```

✅ **Jeremy Bowers = Murderer**

---

### 5. But Wait… Who Hired Him?

Interviewed Jeremy:
```sql
SELECT * 
FROM interview 
WHERE person_id = 67318;
```
He was hired by a **wealthy woman**, around 5'5"-5'7", **red hair**, drives a **Tesla Model S**, attended **SQL Symphony Concert** *three times* in **Dec 2017**.

---

### 6. Tracked the Mastermind 🎭
Queried concert check-ins:
```sql
SELECT person_id 
FROM facebook_event_checkin 
WHERE event_name = 'SQL Symphony Concert' 
AND date LIKE '201712%';
```

Found one person who attended **3 times**:  
**person_id = 99716**

Identified her:
```sql
SELECT * 
FROM person 
WHERE id = 99716;
```
👩 Name: **Miranda Priestly**

Confirmed her car and red hair:
```sql
SELECT * 
FROM drivers_license 
WHERE id = 202298;
```

🎯 **Miranda Priestly = Mastermind**

---

## 🎉 Final Conclusion

- 🔪 **Murderer**: Jeremy Bowers  
- 🧠 **Mastermind**: Miranda Priestly  

SQL City can rest easy now.

---

## 🧠 What I Learned

- How to navigate a relational database step-by-step using logic
- Real-world SQL debugging and investigation strategies
- Importance of cross-referencing data between multiple tables

---

## 🚀 Try It Yourself

💡 Want to sharpen your SQL skills in a fun way?  
Start the challenge here 👉 [https://mystery.knightlab.com/](https://mystery.knightlab.com/)

---
