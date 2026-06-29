# The Ultimate National Cheng Chi University (NCCU) Student Survival Guide: Syllabuddy

The Ultimate National Cheng Chi University (NCCU) 
Student Survival Guide: Syllabuddy

## Project Description

Every new semester at National Chengchi University is a new beginning. Students, especially freshmen, anticipate the opening of the school’s online course selection system so that they can grab the courses they plan to take for the semester. Some students have it together like they are certain about their selected courses and their semester’s overall workload, and they may already have a general idea of how to manage their time. This is the ideal situation that all students wish to have. However, more often than not, students, most especially freshmen, struggle to gauge the weight of the workload relative to the number of selected courses. This issue can be attributed to several factors, such as the differing teaching styles, class schedules, and course requirements. As a result, students are prone to suffer burnout during midterms and finals season due to the lack of adequate pre-semester planning and time management throughout the semester. Currently, the course selection system only provides a week-long schedule based on a student’s selected courses. See Figure 1.1. 
<img width="876" height="974" alt="image" src="https://github.com/user-attachments/assets/863bb4fd-d452-4142-b3c9-3471a05e42e5" />

Although this chart sufficiently provides a general overview of the number of hours and classes a student takes for a semester, it does not provide a detailed description of each class’s workload and the types of assignments that comprise the course. Due to the lack of a unified list, students could only check each course description page one by one to familiarize themselves with the course’s assignments and workloads. 
 
Our AI project, Syllabuddy, aims to address this issue by providing a personalized student activity schedule that tailors to each student's course selection. The project ideally works when it is linked to the school’s course selection system as well as Moodle. However, due to access limitations, we have decided to create a simple prototype of the system instead, utilizing data from the course selection system, specifically the course schedules of 25 English-Medium Instruction (EMI) courses within the International College of Innovation (ICI). 

Syllabuddy is created through python programming on Google Colab, uploading data from course schedules saved on Google Drive to Mongodb, and utilizing Retrieval-Augmented Generation (RAG) to extract course information from Mongodb. It uses a Gradio user interface, and is ultimately deployed as a web application on Hugging Face.


## Getting Started

No downloads are necessary. Simply access Syllabuddy at https://introtoai-group6-syllabuddy.hf.space. It is readily available as a web application. Alternatively, the Google Colab project is available at  https://colab.research.google.com/drive/1sT8u_En_PO6oVbx9r6BZwN46BGEIruye?usp=sharing.
## File Structure
The project consists of the main application (app.py), which contains the Gradio interface, the RAG pipeline, schedule generation, and export functions. The deployment environment on Hugging Face also includes a requirements.txt file that specifies the libraries and dependencies required to run the application.
Our project uses PDF documents as the knowledge base for the RAG system. Each PDF file represents a single course and is named using the course number. Using the course number as the file name provides a unique identifier for each course and helps the retrieval system locate the correct document more efficiently.
Each PDF contains the following information:
+ Course name
+ Course number
+ Class dates
+ Weekly schedule (Week 1 to Week 16)
+ In-class activities (include assignments and exams)

The content of each file is organized chronologically according to the course syllabus. This consistent structure allows the RAG system to retrieve not only the correct course document but also the relevant weekly information when answering user queries.
All course files follow the same format, making them closely related within the knowledge base. The standardized organization enables the system to process documents consistently, compare information across different courses, and retrieve accurate and relevant context for users' questions.


## Analysis

[Describe your analysis methods and include any visualizations or graphics that you used to present your findings. Explain the insights that you gained from your analysis and how they relate to your research question or problem statement.]

## Results

The final output of our project is an interactive study planning tool that allows students to generate a personalized semester schedule based on the courses they choose to enroll in. Rather than requiring students to manually read through every syllabus, the system automatically extracts important deadlines and presents them in a clear, organized format. This enables students to gain an overview of their workload before and during the semester.

After selecting their desired courses, the system uses a RAG model to retrieve information from the corresponding course syllabi and identify key academic events, including assignments and examinations. These tasks are then combined into a single schedule and displayed in a weekly table. Instead of presenting information course by course, the system reorganizes all deadlines into chronological order, allowing students to easily identify when multiple assignments or exams occur during the same week. This provides a much clearer overview of the semester than reading individual syllabi separately. 

To further improve usability, the schedule includes a visual stress indicator for each week. The program calculates a stress score based on the number and type of academic tasks. Examination weeks receive a higher weight than assignment only weeks because exams generally require more preparation time. The results are displayed using a color coded system, where lighter colors represent weeks with a relatively low workload and darker shades of red indicate weeks expected to be more academically demanding. This visual representation allows students to quickly recognize periods of high workload and prepare accordingly by starting assignments earlier or adjusting their study plans.

Recognizing that course schedules often change throughout the semester, our system also provides an editing function. Users are able to manually modify the generated schedule by adding new assignments, changing deadlines, or deleting outdated tasks if instructors announce changes after the semester has begun. Once these edits have been confirmed, the stress visualization is automatically updated to reflect the revised workload. This flexibility ensures that the schedule remains useful throughout the entire semester rather than becoming outdated after the initial course selection.

Finally, students can export their personalized schedule as either a PDF or CSV file. This allows them to download and save their study plan for offline use or import it into other planning tools. By providing an editable and downloadable schedule, the system becomes a practical resource that students can continue using throughout the term rather than simply viewing the information once.  Overall, the results demonstrate that our system successfully transforms large amounts of syllabus information into an accessible and user-friendly planning tool. Instead of manually searching through multiple course documents, students receive a single, organized overview of all important academic deadlines and workload distribution across the semester. This can help improve time management, reduce unexpected deadline conflicts, and support more effective study planning.

## Future Applications
Although the current prototype successfully demonstrates the concept, its main limitation is that the database must be created and maintained manually. Because our system is not connected to NCCU's course selection system or the university's internal databases, the project team must manually collect course syllabi, process them, and upload the information into the RAG database before students can use the application. Whenever instructors update their syllabi or assignment deadlines, the database must also be updated manually by the creators to ensure that the information remains accurate.

In the future, the system could be integrated directly with NCCU's course selection system. Since course information and deadlines are already available before students register for their classes, the RAG system could retrieve this information automatically without requiring the project developers to build and maintain a separate database. As a result, any changes made by instructors such as updated assignment deadlines, newly announced examinations, or revised course schedules would be reflected immediately in the application through automatic database updates.

An additional improvement would be for the university to adopt a standardized syllabus format. Currently, instructors organize their syllabi using different layouts and wording, making it more difficult for the RAG system to consistently identify assignments, examinations, readings, presentations, and other important course activities. By introducing a common template with clearly defined categories, the retrieval process would become more accurate and reliable, improving the overall performance of the system.

With these improvements, the application could serve as a continuously updated academic planning tool, allowing students to view an accurate overview of their semester workload before classes begin and throughout the entire term without requiring manual maintenance by the system developers.

## Contributors
113702013 游婷宇 Vera Yu
114zu1055 闕云宣 Isa Chueh

## Acknowledgments
Special thanks to prof. Pien,  prof. Owen, Yoyo ,Joanne, Neri and Kevin for all the assistance along the way.
