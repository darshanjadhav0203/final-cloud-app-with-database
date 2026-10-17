# Final Project Submission Guide: Add a New Assessment Feature to an Online Course App

This guide contains all responses, GitHub URLs, screenshots, and step-by-step instructions to achieve **100% (15/15 points)** on the Coursera assignment.

---

## Assignment Overview & Grading Criteria

| Task | Description | Max Points | Submission Item |
| :--- | :--- | :---: | :--- |
| **Task 1** | GitHub URL of `models.py` (Question, Choice, Submission models) | **3 points** | URL Link |
| **Task 2** | GitHub URL of `admin.py` (7 imported classes, QuestionInline, ChoiceInline, QuestionAdmin, LessonAdmin) | **3 points** | URL Link |
| **Task 3** | Screenshot of the admin site (`03-admin-site`) displaying Authentication and Authorization + OnlineCourse sections | **1 point** | Image file (`03-admin-site.png`) |
| **Task 4** | GitHub URL of `course_details_bootstrap.html` (course detail template displaying course and lessons with Django tags and Bootstrap) | **2 points** | URL Link |
| **Task 5** | GitHub URL of `views.py` (`submit` and `show_exam_result` functions) | **2 points** | URL Link |
| **Task 6** | GitHub URL of `urls.py` (paths for `submit` and `show_exam_result`) | **2 points** | URL Link |
| **Task 7** | Screenshot of mock exam result (`07-final`) showing successful attempt with 'Congratulations', score, and results | **2 points** | Image file (`07-final.png`) |
| **Total** | | **15 points (100%)** | Passing: 70% (11 points) |

---

## Detailed Task Answers for Submission

### Task 1: GitHub URL of `models.py` (3 points)
- **URL to Submit:**
  ```text
  https://github.com/darshanjadhav0203/final-cloud-app-with-database/blob/master/onlinecourse/models.py
  ```
- **Implemented Models:**
  - `Question`: contains `lesson` (ForeignKey), `course` (ForeignKey), `question_text`, `grade`, and method `is_get_score(selected_ids)`
  - `Choice`: contains `question` (ForeignKey), `choice_text`, `is_correct` (BooleanField)
  - `Submission`: contains `enrollment` (ForeignKey) and `choices` (ManyToManyField)

---

### Task 2: GitHub URL of `admin.py` (3 points)
- **URL to Submit:**
  ```text
  https://github.com/darshanjadhav0203/final-cloud-app-with-database/blob/master/onlinecourse/admin.py
  ```
- **Requirements Implemented:**
  - 7 imported model classes: `Course`, `Lesson`, `Instructor`, `Learner`, `Question`, `Choice`, `Submission`
  - `QuestionInline(admin.StackedInline)`
  - `ChoiceInline(admin.StackedInline)`
  - `LessonAdmin(admin.ModelAdmin)` with `inlines = [QuestionInline]`
  - `QuestionAdmin(admin.ModelAdmin)` with `inlines = [ChoiceInline]`
  - Model registrations for `Course`, `Lesson`, `Instructor`, `Learner`, `Question`, `Choice`, and `Submission`

---

### Task 3: Screenshot of the Admin Site (`03-admin-site`) (1 point)
- **File to Upload:**
  - Local path: `submission_files/03-admin-site.png` (or `03-admin-site.png`)
  - Description: Shows the Django administration site displaying:
    - **AUTHENTICATION AND AUTHORIZATION** section (Groups, Users)
    - **ONLINECOURSE** section (Choices, Courses, Instructors, Learners, Lessons, Questions, Submissions)

---

### Task 4: GitHub URL of `course_details_bootstrap.html` (2 points)
- **URL to Submit:**
  ```text
  https://github.com/darshanjadhav0203/final-cloud-app-with-database/blob/master/onlinecourse/templates/onlinecourse/course_details_bootstrap.html
  ```
  *(Note: An identical copy `course_detail_bootstrap.html` is also available at: `https://github.com/darshanjadhav0203/final-cloud-app-with-database/blob/master/onlinecourse/templates/onlinecourse/course_detail_bootstrap.html`)*
- **Requirements Implemented:**
  - Displays course name and iterated lessons using Django template tags and Bootstrap cards.
  - Collapsible `#exam` section with interactive question form sending POST requests to `onlinecourse:submit`.
  - Checkboxes for choices and submit button.

---

### Task 5: GitHub URL of `views.py` (2 points)
- **URL to Submit:**
  ```text
  https://github.com/darshanjadhav0203/final-cloud-app-with-database/blob/master/onlinecourse/views.py
  ```
- **Requirements Implemented:**
  - `extract_answers(request)`: extracts selected choice IDs from POST parameters
  - `submit(request, course_id)`: creates/retrieves course enrollment, creates a new `Submission` record, attaches selected `Choice` items, and redirects to `show_exam_result`
  - `show_exam_result(request, course_id, submission_id)`: computes question results via `question.is_get_score()`, evaluates percentage grade, and renders `exam_result_bootstrap.html`

---

### Task 6: GitHub URL of `urls.py` (2 points)
- **URL to Submit:**
  ```text
  https://github.com/darshanjadhav0203/final-cloud-app-with-database/blob/master/onlinecourse/urls.py
  ```
- **Requirements Implemented:**
  - `path('<int:course_id>/submit/', views.submit, name='submit')`
  - `path('course/<int:course_id>/submission/<int:submission_id>/result/', views.show_exam_result, name='show_exam_result')`

---

### Task 7: Screenshot of Exam Results (`07-final`) (2 points)
- **File to Upload:**
  - Local path: `submission_files/07-final.png` (or `07-final.png`)
  - Description: Shows the successful mock exam result:
    - Green alert with **"Congratulations, Darshan! You have passed the exam and completed the course with score 100/100."**
    - "Exam results" section with green checkmarks and "Correct" badges for the selected answers.

---

## GitHub Push Note
If you have not yet pushed your local commits to your remote repository:
1. Ensure your remote repository exists at: `https://github.com/darshanjadhav0203/final-cloud-app-with-database`
2. Run in terminal:
   ```bash
   git push -u origin master
   ```
