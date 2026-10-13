# library_Records_Portal
college library Records Portal..




LIBRARY RECORDS PORTAL
Project Report
––
1. Introduction
A library manages books, copies, student details, and borrowing transactions. When these records are maintained manually, staff may need to search registers, calculate due dates, and update stock counts by hand. This project presents a simple Library Records Portal that keeps these tasks together in a browser interface. The design uses a blue-and-white theme and separates the public catalogue from administrative functions.
1.1 Motivation
The motivation for this project is to reduce repetitive record-keeping work and make the status of books easier to understand. A searchable catalogue can help users find titles quickly. For library staff, a single screen for adding books, registering a student, issuing a– copy, and recording a return can reduce missed updates. Automatic due-date calculation and overdue highlighting also make follow-up easier.
1.2 Problem Statement
A small library may keep book information and lending records in separate registers or spreadsheets. Searching for a book, checking the available quantity, tracking who borrowed a copy, and identifying late returns can therefore take time and may lead to inconsistent stock counts. The project addresses this problem by providing a basic, unified interface for catalogue management and issue/return tracking.
1.3 Purpose, Objectives and Goals
•	Create a clear startup page with User Portal and Admin Portal choices.
•	Allow the catalogue to be searched and filtered by relevant book information and availability.
•	Allow an administrator to add, edit, and delete book records, subject to issue-related restrictions.
•	Show dashboard statistics for titles, copies, available stock, active issues, and overdue records.
•	Register student details and record book issue dates and target return dates.
•	Prevent issuing a book when no copy is available and prevent deleting a book with an active issue.
•	Increase available stock when a book is marked as returned.
•	Retain records in the same browser using localStorage.
1.4 Literature Survey
The design follows common concepts from introductory web development and information-system design. HTML forms provide structured data entry; CSS supports responsive layout and visual status labels; JavaScript validates input and updates the interface. Browser Web Storage provides a lightweight way to retain small amounts of data between visits. Database design literature also recommends separating entities such as books, students, and transactions to reduce duplication and support consistent updates. In this project, that separation is represented in the application data structures, although the prototype stores the data as browser-side JSON rather than in a relational database.
The project is informed by the general guidance in the references listed in Section 8. The exact subjects and prescribed editions for B.Com, BBA, and B.Voc (Software Development) vary by institution, so the sample book list should be checked against the college syllabus.
1.5 Project Scope and Limitations
Scope: catalogue search and filtering; book record maintenance; sample inventory for general reading and first-year course reference books; student entry; one-copy issue workflow; due-date calculation at 15 days after the given date; return processing; overdue indicators; and dashboard counts.
Limitations: the application is front-end only; localStorage data is limited to one browser profile and device; there is no server-side database, simultaneous multi-user support, verified login, role-based authorization, barcode scanning, email/SMS reminders, fine calculation, or backup/restore service. The startup role choices are navigation options and are not secure authentication. The current student form uses diploma-stream choices, so institutions using B.Com/BBA/B.Voc programmes may wish to update that field to match their actual student categories.
2. System Analysis
2.1 Existing Systems
Common approaches to library record keeping include paper registers, spreadsheet files, and full library management systems. Paper registers are simple but require manual searching and updating. Spreadsheets allow sorting and filtering but can become difficult to maintain when several people edit copies of the same file. Full library systems can offer centralized records, user accounts, lending rules, reporting, and backups, but may require installation, training, hosting, or licensing.
2.2 Scope and Limitations of Existing Systems
Approach	Advantages	Limitations
Paper registers	Low setup cost; familiar process	Slow searches; manual calculations; difficult reporting; risk of damaged or misplaced records
Spreadsheets	Sorting, filters, basic formulas	Easy to overwrite data; weak transaction controls; limited workflow guidance
Full library system	Central records; richer reporting and account controls	May require a server, training, configuration, or subscription
Proposed prototype	Simple browser interface; no server setup; issue/return workflow	Local to one browser; no secure accounts or central synchronization

2.3 Project Perspective and Features
The project is a small standalone web application. The launch screen directs the user to either a read-only catalogue view or the administrative workspace. The admin workspace contains dashboard, book records, student records, and issue/return records. Book availability is calculated from total and available copies. Issuing a book reduces available stock by one; returning it increases stock by one. A target return date is set to 15 days after the given date, and active issues past that date are marked overdue.
•	Startup screen with User Portal and Admin Portal options
•	Search and availability filters in the catalogue
•	Add, edit, and delete book records
•	Dashboard statistics
•	Student and issue record entry
•	Automatic target return date calculation
•	Return processing and stock adjustment
•	Overdue status highlighting
•	Browser localStorage persistence
•	Sample books for B.Com, BBA, and B.Voc (Software Development)
2.4 Stakeholders
Stakeholder	Interest / Responsibility
Library administrator / librarian	Maintain catalogue, issue books, record returns, review overdue records
Student / library member	Search the catalogue and check whether a book is available
Faculty / project guide	Review whether the project meets academic requirements
College / department	Provide the correct syllabus, borrowing policy, and record conventions
Project developer / student	Implement, test, document, and maintain the prototype

2.5 Requirement Analysis
Functional Requirements
•	FR-01: The application shall show a startup screen with User and Admin navigation options.
•	FR-02: The user shall be able to search and filter book records.
•	FR-03: The admin shall be able to add and edit book details including title, author, category, ISBN, and copy count.
•	FR-04: The admin shall be able to delete a book only when it has no active issue.
•	FR-05: The system shall display dashboard statistics derived from stored book and issue records.
•	FR-06: The system shall allow entry of student name, enrollment/roll number, programme stream, book, and given date.
•	FR-07: The system shall allow a book to be issued only when at least one copy is available.
•	FR-08: On issue, available copies shall decrease by one and the target return date shall be 15 days after the given date.
•	FR-09: On return, the issue status shall change to returned and available copies shall increase by one.
•	FR-10: Active issues past their target return date shall be highlighted as overdue.
•	FR-11: Records shall be saved to browser localStorage and loaded on subsequent visits in the same browser.
Performance Requirements
•	The interface should load without a separate server when opened in a modern browser.
•	Search and filtering should respond promptly for a small college demonstration dataset.
•	The layout should remain usable on desktop and mobile-sized screens.
•	The application should not require external JavaScript or CSS libraries.
Security and Data Requirements
•	Validate required fields and numeric copy values before saving.
•	Do not allow issue transactions when available stock is zero.
•	Do not allow deletion of a book that has an active issue.
•	Treat the role-selection screen as navigation only; it does not provide real access control.
•	Do not store confidential or sensitive student information in a shared/public browser profile.
•	Back up data manually if needed; localStorage can be cleared by browser settings and is not a substitute for a database.
3. Implementation Details: Software and Hardware Specifications
3.1 Software Specifications
Component	Specification
Markup	HTML5
Styling	CSS3 with responsive media queries
Application logic	Vanilla JavaScript
Data persistence	Browser localStorage with JSON serialization
Runtime	Modern web browser such as Chrome, Edge, Firefox, or Safari
External dependencies	None required for the core application
Operating system	Windows, macOS, or Linux capable of running a supported browser

3.2 Hardware Specifications
Minimum practical requirements are a basic desktop or laptop, approximately 2 GB RAM or more, a keyboard and pointing device, and a display capable of showing a modern browser. No dedicated server is required for the demonstration. Actual performance depends on the browser and device.
3.3 Implementation Approach
The application is delivered as a single index.html file containing the HTML, CSS, and JavaScript. HTML defines the screens, forms, tables, and controls. CSS provides the blue-and-white theme, cards, status tags, responsive layout, and overdue styling. JavaScript loads sample records on the first visit, reads and writes localStorage, validates form submissions, updates book and issue tables, and recalculates the visible statistics. The sample inventory includes general titles and reference-book entries for B.Com, BBA, and B.Voc (Software Development). Sample records are illustrative and should be adjusted to the institution’s prescribed syllabus.
4. System Design
4.1 Design Constraints: Normalised Database Design and Data Dictionary
The current implementation does not use a relational database. The following is a proposed logical schema for a future database-backed version. It separates books, students, and issue transactions so that student and book details do not need to be repeated as the authoritative record in every transaction. The current browser implementation stores corresponding objects in localStorage arrays.
Entity / Table	Fields	Purpose
BOOK	book_id (PK), title, author, category, isbn, total_copies, available_copies	One row per catalogue title
STUDENT	student_id (PK), full_name, enrollment_no (unique), programme_stream	One row per registered student
ISSUE	issue_id (PK), student_id (FK), book_id (FK), issue_date, due_date, return_date, status	One row per borrowing transaction
ADMIN (future)	admin_id (PK), username (unique), password_hash, role	Secure admin account management in a server-backed version

Normalisation notes: BOOK stores book-specific attributes; STUDENT stores student-specific attributes; ISSUE links the two entities by keys. Enrollment number should be unique. A transaction should not duplicate the student’s name or book title as its authoritative identity; these values can be retrieved through the related keys. available_copies must remain between zero and total_copies. In a relational implementation, issuing and returning should run in a database transaction to avoid inconsistent stock updates.
Data Dictionary
Field	Type (proposed)	Rules / Description
book_id	VARCHAR / primary key	Unique book identifier
title	VARCHAR(100)	Required book title
author	VARCHAR(80)	Required author/publisher field as used by the form
category	VARCHAR(100)	Required subject or category
isbn	VARCHAR(25)	Optional ISBN
total_copies	INTEGER	Must be at least 1
available_copies	INTEGER	Must be 0 or greater and no greater than total_copies
student_id	VARCHAR / primary key	Unique student record identifier
full_name	VARCHAR(90)	Required student name
enrollment_no	VARCHAR(40)	Required and unique student roll/enrollment number
programme_stream	VARCHAR(100)	Student’s course or stream
issue_id	VARCHAR / primary key	Unique issue transaction identifier
issue_date	DATE	Date the copy is issued
due_date	DATE	Issue date plus 15 days in this prototype
return_date	DATE, nullable	Blank until the copy is returned
status	ENUM / VARCHAR	Issued or Returned; overdue is derived from status and due date

4.2 Data Model: FDD Diagram
The following Functional Decomposition Diagram (FDD) shows the main functions of the application:
LIBRARY RECORDS PORTAL
│
├── Startup / Role Selection
│   ├── User Portal
│   │   ├── Browse Catalogue
│   │   ├── Search Books
│   │   └── Filter by Availability
│   └── Admin Portal
       ├── Dashboard Statistics
       ├── Book Management
       │   ├── Add / Edit Books
       │   ├── Search / Filter Records
       │   └── Delete if No Active Issue
       ├── Student Records
       │   ├── Enter Student Details
       │   └── Issue Available Book
       └── Issue / Return Management
           ├── Calculate Due Date (+15 Days)
           ├── Highlight Overdue Issues
           └── Return Book and Update Stock
4.3 User Interfaces
The interface uses a consistent blue-and-white visual theme. Navigation labels and page headings identify the current area. Tables display records in a compact format, while status tags distinguish available, issued, returned, and overdue states. The application is responsive, so the sidebar and grids adapt on smaller screens.
4.3.1 Menus
•	Startup screen: User Portal and Admin Portal.
•	User Portal: book catalogue, search field, availability filter, and return-to-start button.
•	Admin Dashboard: summary cards and overview of current library activity.
•	Book Records: search/filter controls, add-book form, and edit/delete actions.
•	Student Records: student and issue form, student/issue search, status filter, and return action.
•	Issue / Return Records: list of active and returned transactions, due dates, status, and return action.
4.3.2 Input Screens Using Sample Data
Book entry screen sample: Book Name = “Business Economics: Microeconomics”; Author = “H. L. Ahuja”; Category = “B.Com · Business Economics”; ISBN = blank; Total Copies = 4. The form requires the title, author, category, and a valid positive total-copy value.
Student and issue screen sample: Student Name = “Aarav Sharma”; Enrollment ID = “DPL-2026-015”; Diploma Program Stream = “Computer Engineering”; Book Name = “Programming in ANSI C”; Book Given Date = 13 October 2026; Target Return Date = 28 October 2026. These are illustrative test values, not actual student records. The book can only be selected for issue if its available-copy count is greater than zero.
4.3.3 Output Screens
•	Dashboard: summary cards for total titles/copies, available stock, active issues, and overdue items.
•	Book Records: a searchable table showing book identifier, title, author, category, total copies, available copies, and actions.
•	Student Records: a table showing student, enrollment ID, stream, book, given date, target return date, status, and return action.
•	User catalogue: cards for book titles and authors with an availability indicator.
•	Issue/Return Records: transaction list with due date and current status; overdue items receive a visual warning.
4.3.4 Reports and Graphs Using Sample Data
The current interface provides dashboard statistics and status-based tables rather than a dedicated chart/report export module. The following example illustrates how dashboard counts can be calculated from the initial sample catalogue. These counts describe the seeded sample books before any transactions and are not live results from a populated college library.
Sample metric	Value	Meaning
Book titles	25	Number of seeded catalogue records
Total copies	105	Sum of total copies across seeded titles
Available copies	93	Sum of available copies before any new transactions
Issued copies	12	Difference between total and available copies in the initial seeded inventory
Overdue issues	0	No overdue transactions are seeded by default

Note: The figures above are a manually derived illustration based on the current sample inventory. The application’s dashboard should be used to view the current counts after records have been changed. A future version could add monthly issue/return charts, course-wise book counts, and CSV/PDF reports.
5. Testing
Testing should confirm both input validation and the expected workflow. The table below is a proposed test plan for the project. Before submission, run each case in the final browser version and replace “Expected” with the observed result and pass/fail status. Do not report a case as passed unless it has actually been executed.
5.1 Black Box Testing / Data Validation Test Cases
Test ID	Input / Action	Expected Result	Observed Result / Status
BB-01	Search for a known title, e.g. “Wings of Fire”	Matching book record is shown	To be tested
BB-02	Filter catalogue to “Available only”	Only books with available copies are shown	To be tested
BB-03	Submit a book form with required fields empty	Form blocks submission and indicates required fields	To be tested
BB-04	Enter total copies as 0 or a negative value	Input validation rejects the value	To be tested
BB-05	Attempt to issue a book with zero available copies	Issue is blocked; stock does not become negative	To be tested
BB-06	Issue an available book using a valid student and date	Issue is recorded; available stock decreases by one	To be tested
BB-07	Set given date to 13 Oct 2026	Target return date becomes 28 Oct 2026	To be tested
BB-08	Return an active issue	Status becomes Returned; available stock increases by one	To be tested
BB-09	Attempt to delete a book with an active issue	Deletion is blocked	To be tested
BB-10	Use an issue whose due date is before today and status is Issued	Record is highlighted as overdue	To be tested
BB-11	Reload the same browser after saving a record	Saved data remains available in that browser	To be tested
BB-12	Open project on another browser/device	Local data is not assumed to synchronize	To be tested

5.2 White Box Testing / Functional Validation Test Cases
Test ID	Logic / Condition	Expected Result	Observed Result / Status
WB-01	available_copies > 0 before issue	Issue path continues only when a copy exists	To be tested
WB-02	available_copies == 0 before issue	Issue path exits without creating an issue	To be tested
WB-03	Issue saved successfully	available_copies is reduced by exactly 1	To be tested
WB-04	Issue status changes from Issued to Returned	available_copies is increased exactly once	To be tested
WB-05	Book has an active issue	Delete condition rejects deletion	To be tested
WB-06	Due date is earlier than current date and status is Issued	Overdue condition evaluates true	To be tested
WB-07	Due date is today or later	Issue is not marked overdue	To be tested
WB-08	Records are written and then loaded from localStorage	JSON records are restored after reload	To be tested

5.3 Test Environment and Results
Suggested environment: a current version of Chrome, Edge, Firefox, or Safari on a desktop/laptop, with the application opened from the downloaded index.html file. Use a separate browser profile or clear the project’s localStorage keys before testing first-run sample data. Because this report was prepared from the implementation design and not from a recorded formal test session, actual pass/fail results must be entered by the student after running the cases.
6. Conclusion and Recommendations
The Library Records Portal demonstrates how a small library’s routine tasks can be grouped into one browser-based interface. It includes catalogue search and filtering, book record management, dashboard statistics, student and issue records, due-date calculation, overdue highlighting, and stock updates on issue and return. The initial catalogue contains sample general titles and first-year reference entries for B.Com, BBA, and B.Voc (Software Development).
The project is suitable as an introductory front-end academic prototype. Before using it for real institutional records, the college should verify the subject list, add proper authentication, use a central database, implement backups, and test the issue/return rules thoroughly. The current User/Admin screen should not be treated as a security boundary.
7. Future Scope
•	Connect the interface to a relational database such as MySQL or PostgreSQL through a server-side API.
•	Add secure login, password hashing, sessions, and role-based permissions for administrators and users.
•	Add book cover images, barcode/QR scanning, and ISBN lookup.
•	Generate downloadable CSV, PDF, and print-friendly reports.
•	Add email or SMS reminders before and after due dates, plus optional fine calculations.
•	Support multiple copies with copy-level identifiers and full transaction history.
•	Add data backup, restore, audit logs, and duplicate-record checks.
•	Add course/semester filters and maintain book lists against the official syllabus for each programme.
•	Deploy the application on a college network with access controls and privacy safeguards.
8. Bibliography and References
[1] MDN Web Docs, “HTML: HyperText Markup Language.” https://developer.mozilla.org/en-US/docs/Web/HTML (accessed 13 October 2026).
[2] MDN Web Docs, “CSS: Cascading Style Sheets.” https://developer.mozilla.org/en-US/docs/Web/CSS (accessed 13 October 2026).
[3] MDN Web Docs, “JavaScript.” https://developer.mozilla.org/en-US/docs/Web/JavaScript (accessed 13 October 2026).
[4] MDN Web Docs, “Window: localStorage property.” https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage (accessed 13 October 2026).
[5] MDN Web Docs, “Client-side form validation.” https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation (accessed 13 October 2026).
[6] Elmasri, R. and Navathe, S. B., Fundamentals of Database Systems, Pearson. Refer to the edition available through the college library.
[7] Sommerville, I., Software Engineering, Pearson. Refer to the edition prescribed by the course.
[8] Library Records Portal, project implementation file: index.html, student-developed front-end prototype, 2026.
Appendix A: Submission Checklist
•	Replace all cover-page placeholders with the student’s actual details.
•	Confirm the project title and course name with the faculty guide.
•	Check sample subject titles and book editions against the college syllabus.
•	Run and document all test cases in Section 5.
•	Add screenshots of the actual startup screen, dashboard, book records, and issue/return page if required by the college.
•	Follow the college’s formatting, citation, and declaration requirements.
