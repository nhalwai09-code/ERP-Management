# College ERP Management System

A web-based **College Enterprise Resource Planning (ERP) Management System** designed for academic institutions to manage day-to-day college activities across **Administrators**, **Faculty**, and **Students** in a centralized environment.

Developed as a Third Year Computer Science (TYCS) Mini Project using **PHP 8+**, **MySQL**, **Bootstrap 5**, and **JavaScript**, running locally under **XAMPP**.

---

## 🌐 Live Local URL

The application is deployed and actively running at:
```
http://localhost/college_erp/
```

Workspace path:
```
C:\Users\Admin\.gemini\antigravity\scratch\college_erp\
```
*(Linked to XAMPP document root at `C:\xampp\htdocs\college_erp\`)*

---

## 🔑 Default Login Credentials

| Role | Email / Registration ID / Username | Password | Access Rights |
| :--- | :--- | :--- | :--- |
| **ADMIN** | `admin@college.com` | `admin123` | Full CRUD access to all modules, master records, finance, exams, and notices |
| **FACULTY** | `faculty@college.com` | `faculty123` | View students, record class attendance, enter/edit marks, view exams & notices |
| **STUDENT** | `student@college.com` *or* `REG2026001` | `student123` | View own profile, personal attendance %, fee ledger & receipt, exam marksheets |

> **Pro Tip for Viva:** 
> - **Student Self-Registration First:** The authentication page loads **Student Registration First** by default (`login.php?tab=register` or `register.php`), allowing any new student to self-register, immediately obtain their unique official **Registration ID** (e.g. `REG2026005`), and then sign in.
> - The login page (`login.php`) supports logging in using **Email**, **Official Registration ID** (e.g., `REG2026001`), or **Student Code** (`STU101`).
> - Includes **one-click demo buttons** to instantly populate credentials for Admin, Faculty, and Student accounts without manual typing.

---

## 📁 Project Directory Structure

```text
college_erp/
├── config/
│   └── db.php                  # PDO MySQL connection, session initialization, helpers
├── includes/
│   ├── auth_check.php          # Role-based access control (RBAC), redirection guards
│   ├── header.php              # Bootstrap 5 CDN, Bootstrap Icons, custom typography
│   ├── navbar.php              # Top bar, active session, role badges, alerts
│   ├── sidebar.php             # Role-aware collapsible navigation sidebar
│   └── footer.php              # Layout closing tags, scripts, copyright footer
├── assets/
│   ├── css/
│   │   └── style.css           # Custom styles, badge pills, responsive cards, print CSS
│   └── js/
│       └── main.js             # Delete confirmations, dynamic fee & marks calculators
├── admin/
│   ├── dashboard.php           # Admin overview, 7 summary metric cards, recent logs
│   ├── students.php            # Student list, multi-field search & filters, delete
│   ├── student_add.php         # Student admission form & automatic user account creation
│   ├── student_edit.php        # Modify student details & synced login credentials
│   ├── student_view.php        # Comprehensive profile, attendance & results history
│   ├── faculty.php             # Faculty directory, search, filter, delete
│   ├── faculty_add.php         # Faculty registration with user account generation
│   ├── faculty_edit.php        # Update faculty credentials & subject handled
│   ├── faculty_view.php        # Faculty profile & lecture workload stats
│   ├── subjects.php            # Subject management, search, course & semester filters
│   ├── subject_add.php         # Add subject yourself with code suggestion & validation
│   ├── subject_edit.php        # Edit curriculum subject details
│   ├── attendance.php          # Attendance registry, filter by student/subject/date
│   ├── attendance_add.php      # Class batch roll call marking & individual entry
│   ├── attendance_edit.php     # Modify existing attendance status
│   ├── fees.php                # Fee management, summary cards, payment filters
│   ├── fees_add.php            # Record fee transaction with auto balance computation
│   ├── fees_edit.php           # Edit fee payment details
│   ├── fees_view.php           # Official printable fee acknowledgement receipt
│   ├── exams.php               # Schedule examination sessions (Internal/Sem/Practical)
│   ├── exam_add.php            # Add new exam timetable entry
│   ├── exam_edit.php           # Edit examination details
│   ├── marks.php               # Result management, pass rate metrics, grade ledger
│   ├── marks_add.php           # Enter student scores with auto grade & pass/fail calculation
│   ├── marks_edit.php          # Update marks with instant recalculation
│   ├── marks_view.php          # Official printable statement of marks / marksheet
│   ├── notices.php             # Notice board management, audience filters
│   ├── notice_add.php          # Publish new circular to campus
│   └── notice_edit.php         # Edit existing notice
├── faculty/
│   ├── dashboard.php           # Faculty metrics (Total students, attendance summary, exams)
│   ├── profile.php             # View and update personal academic profile
│   ├── students.php            # Read-only student directory with search & filters
│   ├── student_view.php        # Student profile and academic performance view
│   ├── subjects.php            # Browse curriculum subjects directory
│   ├── subject_add.php         # Faculty can add subject yourself
│   ├── attendance.php          # View & filter class attendance records
│   ├── attendance_add.php      # Roll call attendance entry (batch & single mode)
│   ├── attendance_edit.php     # Update attendance record status
│   ├── exams.php               # Upcoming exam schedule view
│   ├── marks.php               # Enter & manage student marks
│   ├── marks_add.php           # Marks entry form with auto-grading
│   ├── marks_edit.php          # Edit student scores
│   ├── marks_view.php          # View printable marksheet
│   └── notices.php             # View notices targeted to Faculty and All
├── student/
│   ├── dashboard.php           # Student metrics (Attendance %, fee status, latest result)
│   ├── profile.php             # View own profile and update contact details
│   ├── attendance.php          # Own attendance rate, subject breakdown, lecture log
│   ├── fees.php                # Own fee ledger, payment history, and receipt link
│   ├── fees_view.php           # View own official printable fee receipt
│   ├── results.php             # Own exam performance, grade cards, results summary
│   ├── marks_view.php          # View own official printable statement of marks
│   └── notices.php             # View notices targeted to Students and All
├── index.php                   # Entry router redirecting to correct dashboard
├── register.php                # Student self-registration gateway
├── login.php                   # Authentication portal (Register First & Sign In tabs)
├── logout.php                  # Secure session destruction
├── database.sql                # Complete MySQL SQL schema and test records
├── database_sqlite.sql         # Pure SQLite SQL schema & converted data dump
├── college_erp.sqlite          # Standalone SQLite 3 database file (All 11 tables & live records)
├── convert_to_sqlite.php       # Real-time MySQL-to-SQLite synchronization script
└── README.md                   # Documentation and viva defense guide
```

---

## 🗄️ Database Architecture (MySQL & SQLite Dual Engine)

The system supports **both MySQL and SQLite** out of the box. You can easily switch between them in [`config/db.php`](file:///C:/xampp/htdocs/college_erp/config/db.php):

```php
// Choose database driver: 'mysql' or 'sqlite'
define('DB_DRIVER', 'mysql'); // change to 'sqlite' to run standalone without MySQL!
```

> **Automatic Fallback:** If `DB_DRIVER` is set to `'mysql'` but the MySQL server in XAMPP is stopped, the application automatically falls back to `college_erp.sqlite` without throwing fatal errors!

### SQLite Database Files:
1. **Live SQLite Database File:** `C:\xampp\htdocs\college_erp\college_erp.sqlite`
2. **SQLite SQL Dump Script:** `C:\xampp\htdocs\college_erp\database_sqlite.sql`
3. **Database Re-Sync Utility:** Run `php convert_to_sqlite.php` anytime to sync new data from MySQL to SQLite.

The database consists of 11 normalized relational tables:

1. **`users`**: Central authentication table storing `id`, `name`, `email` (unique), `password` (bcrypt hash via `password_hash()`), `role` (`admin`, `faculty`, `student`).
2. **`students`**: Stores student identity, **`registration_id` (unique, e.g., `REG2026001`)**, `student_code` (unique, e.g., `STU101`), `full_name`, `gender`, `dob`, `address`, `department`, `course`, `year`, `division`, `roll_number`, `admission_date`, and foreign key `user_id`. Supports login via Registration ID.
3. **`faculty`**: Stores `faculty_code`, `full_name`, `email`, `phone`, `gender`, `department`, `qualification`, `subject`, `joining_date`, and foreign key `user_id`.
4. **`departments`**: Academic faculties/departments under NEP 2020 with `department_code`, `department_name`, `faculty_stream`, `description`.
5. **`courses`**: Degree and honors programs offered department-wise under NEP 2020 with `department_id`, `course_code`, `course_name`, `nep_level`, `duration_years`, `total_semesters`, `degree_type`.
6. **`subjects`**: Stores curriculum subjects with `subject_code` (unique), `subject_name`, `department`, `course`, `semester`. Pre-populated with the **entire institutional 3-Year B.Sc. Computer Science curriculum (40 subjects across Semesters I to VI)** plus foundational NEP subjects across all 5 departments.
7. **`attendance`**: Stores daily lecture tracking with `student_id`, `subject`, `attendance_date`, `status` (`Present` / `Absent`).
8. **`fees`**: Stores student fee transactions with `academic_year`, `total_fees`, `paid_amount`, `pending_amount`, `payment_date`, `payment_status` (`Paid`, `Partially Paid`, `Pending`).
9. **`exams`**: Stores scheduled exams with `exam_name`, `exam_type` (`Internal Exam`, `Semester Exam`, `Practical Exam`), `course`, `semester`, `subject`, `exam_date`.
10. **`marks`**: Stores student academic evaluation with `student_id`, `exam_id`, `subject`, `max_marks`, `obtained_marks`, `percentage`, `grade`, `result_status` (`Pass` / `Fail`).
11. **`notices`**: Stores campus circulars with `title`, `description`, `posted_date`, `posted_by`, `target_audience` (`All`, `Students`, `Faculty`).

---

## 🏛️ Department-Wise Courses Architecture (NEP 2020 Rules)

Under the **National Education Policy (NEP 2020)** guidelines issued by the UGC and university academic councils, programs are structured into **5 Academic Departments** featuring 4-Year Undergraduate Honours degrees, multi-disciplinary pathways, and multiple entry/exit credit benchmarks:

| Academic Department | Stream | Course Code | Degree / Program Name | NEP Framework Level | Duration |
| :--- | :--- | :--- | :--- | :--- | :---: |
| **Computer Science** | Science & Technology | `BSC-CS` | B.Sc. Computer Science | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BSC-DSAI` | B.Sc. Data Science & Artificial Intelligence | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BSC-CSDF` | B.Sc. Cyber Security & Forensics | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BCA` | Bachelor of Computer Applications (BCA) | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `MSC-CS` | M.Sc. Computer Science | Level 6.5 (PG 2-Year) | 2 Yrs / 4 Sem |
| **Information Technology** | Science & Technology | `BSC-IT` | B.Sc. Information Technology | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BSC-SDCC` | B.Sc. Software Development & Cloud Computing | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BSC-IOT` | B.Sc. Internet of Things (IoT) & Smart Systems | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `MSC-IT` | M.Sc. Information Technology | Level 6.5 (PG 2-Year) | 2 Yrs / 4 Sem |
| **Commerce & Management** | Commerce & Management | `BCOM` | Bachelor of Commerce (B.Com) | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BAF` | B.Com. Accounting & Finance (BAF) | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BBI` | B.Com. Banking & Insurance (BBI) | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BFM` | B.Com. Financial Markets (BFM) | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BMS` | Bachelor of Management Studies (BMS / BBA) | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `MCOM` | Master of Commerce (M.Com) | Level 6.5 (PG 2-Year) | 2 Yrs / 4 Sem |
| **Science** | Science & Technology | `BSC-PHY` | B.Sc. Physics | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BSC-CHEM` | B.Sc. Chemistry | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BSC-MATH` | B.Sc. Mathematics & Statistics | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BSC-BT` | B.Sc. Biotechnology | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BSC-MB` | B.Sc. Microbiology | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| **Arts & Humanities** | Humanities & Social Sciences | `BA-GEN` | Bachelor of Arts (B.A. General) | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BA-ENG` | B.A. English Literature | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BA-PSY` | B.A. Psychology | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BA-ECO` | B.A. Economics | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |
| | | `BAMMC` | B.A. Multimedia & Mass Communication (BAMMC) | Level 4.5 – 6.0 (UG 4-Yr Honours) | 4 Yrs / 8 Sem |

### 🎯 NEP 2020 Multi-Entry & Multi-Exit Progression:
- **Year 1 (Sem I & II)**: Exit with **UG Certificate** (Level 4.5)
- **Year 2 (Sem III & IV)**: Exit with **UG Diploma** (Level 5.0)
- **Year 3 (Sem V & VI)**: Exit with **Bachelor's Degree** (Level 5.5)
- **Year 4 (Sem VII & VIII)**: Awarded **Bachelor's Degree with Honours / Research** (Level 6.0)
- **Postgraduate (PG 2-Yr)**: **Master's Degree** (Level 6.5)

---

## 📚 Complete B.Sc. Computer Science Curriculum (40 Subjects)

The database includes the standard university B.Sc. Computer Science curriculum across all 3 academic years and 6 semesters:

| Year & Semester | Code | Subject Name |
| :--- | :--- | :--- |
| **FYCS - Sem I** | `CS101` – `CS107` | Computer Organization & Design, Programming with Python - I, Free & Open Source Software, Database Systems Fundamentals, Discrete Mathematics, Descriptive Statistics, Soft Skills Development |
| **FYCS - Sem II** | `CS201` – `CS207` | Programming with C, Programming with Python - II, Linux Operating System, Data Structures, Calculus & Mathematical Methods, Statistical Methods & Testing, Green Technologies |
| **SYCS - Sem III** | `CS301` – `CS306` | Principles of Operating Systems, Core Java Programming, Database Management Systems (Advanced), Combinatorics & Graph Theory, Physical Computing & IoT Programming, Web Programming & Scripting |
| **SYCS - Sem IV** | `CS401` – `CS406` | Fundamentals of Algorithms, Advanced Java Programming, Computer Networks & Protocols, Software Engineering Principles, Linear Algebra, .NET Technologies with C# |
| **TYCS - Sem V** | `CS501` – `CS508` | Web Technologies, Database Systems, Software Engineering, Python Programming, Computer Networks, Artificial Intelligence, Machine Learning & Data Mining, Linux Server Administration |
| **TYCS - Sem VI** | `CS601` – `CS606` | Cloud Computing, Cyber Forensics & Information Security, Information Retrieval, Data Science & Big Data Analytics, Ethical Hacking, Project Implementation & Viva |

---

## 🧮 Mathematical Formulas & Logic Implemented

### 1. Attendance Percentage Calculation
$$\text{Attendance Percentage} = \left(\frac{\text{Present Classes}}{\text{Total Classes}}\right) \times 100$$
- Automatically computed across all records or on a per-subject basis.
- If attendance falls below **75%**, a warning badge/alert is displayed to the student.

### 2. Fees Outstanding Calculation
$$\text{Pending Amount} = \text{Total Fees} - \text{Paid Amount}$$
- Automatically calculated in real-time on input and verified on backend.
- Payment Status auto-resolved:
  - If $\text{Paid} \ge \text{Total} \implies \textbf{Paid}$
  - If $\text{Paid} > 0 \text{ and } \text{Pending} > 0 \implies \textbf{Partially Paid}$
  - If $\text{Paid} = 0 \implies \textbf{Pending}$

### 3. Exam Percentage, Letter Grade & Result Calculation
$$\text{Percentage} = \left(\frac{\text{Obtained Marks}}{\text{Maximum Marks}}\right) \times 100$$

**Grading Scale:**
| Percentage Range | Grade | Description |
| :--- | :---: | :--- |
| **90% – 100%** | **A+** | Outstanding |
| **80% – 89%** | **A** | Excellent |
| **70% – 79%** | **B** | Good |
| **60% – 69%** | **C** | Average |
| **50% – 59%** | **D** | Pass |
| **Below 50%** | **F** | Fail |

**Result Status:**
- $\ge 50\% \implies \textbf{Pass}$
- $< 50\% \implies \textbf{Fail}$

---

## 🛡️ Security & Role-Based Access Control (RBAC)

1. **Password Hashing**: Passwords stored using PHP `password_hash($pwd, PASSWORD_DEFAULT)` and verified using `password_verify($pwd, $hash)`.
2. **SQL Injection Defense**: 100% of database interactions use **PDO Prepared Statements** with parameterized queries (`$stmt->prepare(...)` and `$stmt->execute(...)`).
3. **Cross-Site Scripting (XSS) Prevention**: All user-supplied inputs and query outputs sanitized through `htmlspecialchars($data, ENT_QUOTES, 'UTF-8')`.
4. **Protected Pages & URL Guards**: Every module verifies role permissions (`$allowed_roles`). Unauthorized access attempts automatically redirect users back to their respective dashboards with a notification.
5. **Data Privacy**: Students can **only** view their own fee receipts, attendance summaries, and marksheets. Queries enforce `WHERE student_id = :session_student_id`.

---

## 🎓 College Viva Preparation Q&A

**Q1: What architecture does this project follow?**
> It follows a clean modular PHP architecture where database configuration, reusable partials (header, sidebar, navbar, footer), role guards, and controllers are structured cleanly. Each role (Admin, Faculty, Student) has dedicated controllers and views.

**Q2: How is session security maintained?**
> When a user logs in, their credentials are validated using `password_verify()`. If valid, session variables (`user_id`, `user_role`, `user_name`) are created. On every protected page, `auth_check.php` verifies that the active session matches permitted roles. Logging out clears `$_SESSION`, expires the session cookie, and invokes `session_destroy()`.

**Q3: How are relational deletions handled?**
> Foreign keys in MySQL enforce referential integrity with `ON DELETE CASCADE` on transaction tables (`attendance`, `marks`, `fees`), ensuring when a student record is removed, orphan records are deleted cleanly.
