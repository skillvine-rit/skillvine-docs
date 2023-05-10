```
Student login

1. User selects "Login as student".
2. Student logs in with their institution email.
3. Client sends request to server at api/auth/students/.
4. Server checks if student exists in database. If not, redirect student to a data collection form to enter admission number, KTU ID, and name. Server updates student collection in database.
5. Server generates access token for student.
6. Server redirects student to dashboard using access token for subsequent requests.
```

```
Teacher login

1. User selects "Login as teacher".
2. Teacher logs in with their institution email.
3. Client sends request to server at api/auth/teacher.
4. Server checks if teacher exists in database. If not, create teacher in collection.
5. Server generates access token for teacher.
6. Server redirects teacher to student select page using access token for subsequent requests.
```

```
Student Dashboard

1. Student logs in and is redirected to dashboard.
2. Client sends GET request to server for notifications at api/students/notifications.
3. Client displays notifications on the notification panel.
4. Sidebar displays button to fetch student's current activity points.
5. Client sends GET request to server at api/students/score and displays score in sidebar.
6. Student can navigate to all pages from navbar on the left.
```

```
Teacher Dashboard
1. Teacher logs in and is redirected to dashboard.
2. Client sends GET request to server for all batches in database at api/batches.
3. Client displays all batches on UI.
4. Teacher selects a batch.
5. Client sends GET request to server for all students in that batch at api/batches/{batchID}.
6. Teacher selects a student.
7. Client sends GET request to server for all certificates of that student at api/certificates/{studentID}.
8. Client displays a page where all certificates are listed year-wise.
```

```
Student adding a certificate

1. Student selects "Add Certificate" from dashboard.
2. Client sends GET request to server to fetch all available activities and categories of events.
3. Client displays available activities, categories of certificates in dropdown menus for student to select from.
4. Student selects certificate to add and enters required fields: student ID, certificate name, description, date, and any additional information.
5. Client sends new certificate data as POST request to server at api/certificates.
6. Server updates student's certificate collection with new certificate.
7. Server sends response to client indicating success or failure of certificate addition.
```

```
Student or Teacher viewing a certificate

1. Student or teacher navigates to the certificates page.
2. User clicks on a certificate.
3. If specific certificate is selected, client sends GET request to server for certificate details at api/certificates/{certificateID}.
4. Server returns details of selected certificate.
5. Client displays selected certificate's details on separate page.
```

```
Teacher generating report

1. Teacher navigates to report generation page.
2. Client sends GET request to server to fetch all available batches at api/batches.
3. Server returns all available batches.
4. Client displays all batches in dropdown menu for teacher to select from.
5. Teacher selects a batch.
6. If teacher clicks on "Generate Report":
    6.1 Client sends GET request to server to fetch details for selected batch at api/reports/batches/{batchID}.
    6.2 Client generates report based on data sent from server and creates PDF report.
    6.3 Client displays generated report on separate PDF page and allows download.
7. Else the client sends a GET request to server to fetch students at api/batches/{batchID}.
    7.1 The client displays all students in a dropdown menu for the teacher to select from.
    7.2 If teacher clicks on generate report here,
    7.3 The client sends a GET request to server to fetch details for the selected student at api/reports/students/{studentID}.
    7.4 The client generates the report based on the data sent from server and makes a PDF report.
    7.5 The client displays the generated report on a separate PDF page and can download if they want.
```
