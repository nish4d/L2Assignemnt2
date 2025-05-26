# L2Assignemnt2 Q&A

# What is PostgreSQL?

PostgreSQL একটি রিলেশনাল টেবিল ডেটাবেস ম্যানেজমেন্ট সিস্টেম এবং এটি ওপেন সোর্স । এটি বড় মাপের অ্যাপ্লিকেশন, ওয়েব সার্ভিস, এবং বিশেষ কাজের জন্য ব্যবহার  করা হয়। 

---

## Explain the Primary Key and Foreign Key concepts in PostgreSQL.

Primary key - এমন একটি কলাম যেটি সব টেবিল এর রো  গুলাকে ইউনিক করতে সাহায্য করে । 


Example:
```sql
CREATE TABLE users (
  user_id SERIAL PRIMARY KEY,
  username VARCHAR(50)
);
```

Foreign key - এমন একটি কলাম যা অন্য টেবিলের প্রাইমারি কী-এর সাথে সম্পর্ক তৈরি করতে সাহায্য করে । 

Example:
```sql
CREATE TABLE orders (
  order_id SERIAL PRIMARY KEY,
  user_id INT REFERENCES users(user_id)
);
```

---

## Explain the purpose of the WHERE clause in a SELECT statement.

SELECT স্টেটমেন্টে WHERE এর কাজ হল SELECT এর ভিতর নির্দিষ্ট শর্ত অনুসারে তথ্য ফিল্টার করা ।
Example:
```sql
SELECT * FROM rangers
WHERE region = 'Mountain Range';
```

---

## How can you modify data using UPDATE statements?

আপডেট হল কোন টেবিল এর ডাটা পরিবর্তন করার জন্য ব্যবহার করা হয় । 
Example:
```sql
UPDATE species
SET conservation_status = 'Historic'
WHERE discovery_date < '1800-01-01';
```

---

## What is the significance of the JOIN operation, and how does it work in PostgreSQL?

JOIN ব্যবহার করা হয় দুটি বা তার বেশি টেবিলের ডেটা একসাথে আনার জন্য,  একটি টেবিলে যদি ব্যবহারকারীর তথ্য থাকে এবং অন্য টেবিলে তাদের অর্ডার থাকে, তাহলে JOIN ব্যবহার করে জানা যাবে কোন ব্যবহারকারী কোন অর্ডার দিয়েছেন ।
Example:
```sql
SELECT users.username, orders.product
FROM users
INNER JOIN orders ON users.user_id = orders.user_id;
```
