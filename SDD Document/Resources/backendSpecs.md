Category Collection.
The Category collection contains data on the points for each of the activities that students can participate in, following KTU guidelines and point allotment chart.

1. activityHead: {type: String}; required
2. activity: {type: String}; required
3. isLeadership: {type: Boolean}; default false
4. activityPoints: {type: Object};
   level1: {type: Number}
   level2: {type: Number}
   level3: {type: Number}
   level4: {type: Number}
   level5: {type: Number}
5. leadershipPoints: {type: Object};
   coreCoordinator: {type: Number}; default null
   subCoordinator: {type: Number}; default null
   volunteer: {type: Number}; default null
6. maxPoints: {type: Number}; required
7. minDuration: {type: Number}; required

Student Collection
The Student collection stores information about the students.

1. name: {type: String}; student's name; required
2. email: {type: String}; student's email address; required; unique
3. ktuId: {type: String}; KTU Id of the student; unique
4. college: {type: String}; student's college; required; default 'RIT, Kottayam'
5. admissionNumber: {type: String}; student's admission number; unique
6. batch: {type: String}; student's batch
7. profileImage: {type: String}; URL of the student's profile image; default '' (empty string)

Teacher Collection
The Teacher collection stores information about the teachers registered in the system.

1. name: {type: String}; name of the teacher; required
2. email: {type: String}; email of the teacher; required, unique
3. password: {type: String}; password of the teacher; required

Certificate Collection
The Certificate collection stores information about certificates submitted by students for completing different activities.

1. categoryId: {type: mongoose.Schema.Types.ObjectId}; reference to Category Collection
2. certificateName: {type: String}; name or title of certificate; required
3. studentId: {type: mongoose.Schema.Types.ObjectId}; reference to Student Collection; required
4. level: {type: Number}; default 0
5. points: {type: Number}
6. duration: {type: Number}; required
7. year: {type: Number}; required
8. status: {type: String}; 'pending', 'approved', 'rejected', or 'unapplied'; default 'pending'
9. certificateUrl: {type: String}; required
10. certificateDescription: {type: String}; required
11. lastVerifiedBy: {type: mongoose.Schema.Types.ObjectId}; reference to Teacher Collection; default null
12. participationDate: {type: Date}; required
13. leadershipLevel: {type: Number}; default 0
14. isLeadership: {type: Boolean}; default false
15. remarks: {type: String}; default '' (empty string)

Notification Collection
The Notification collection stores the notifications sent to students.

1. studentId: {type: mongoose.Types.ObjectId}; reference to Student Collection
2. message: {type: String}; notification message; required

Score Collection
The Score collection stores information about the scores of students.

1. targetScore: {type: Number}; default value is 100
2. currentScore: {type: Number}; default value is 0
3. studentId: {type: mongoose.Types.ObjectId}; reference to Student Collection
