# Lab 6


1.	Create interfaces  
    1.1.	Create Student interface with fields:   
        1.1.1.	id: string (guid, generated using https://www.npmjs.com/package/uuid )   
        1.1.2.	firstName: string  
        1.1.3.	lastName: string,  
        1.1.4.	personalNumber: string,  
    1.2.	Create StudentFilter interface with fileds  
        1.2.1.	firstName  
        1.2.2.	lastName  
        1.2.3.	personalNumber  
    1.3.	Create SearchOptions interface with following fields  
        1.3.1.	enableTotalRecordsLimit: boolean  
        1.3.2.	maxSearchResultItemCount: number  
2.	Create StudentsService class with private property which will hold students list (as array). Implement following methods:  
    2.1.	validatePersonalNumber(personalNumber: string) Promise<boolean> (for async validation)  
Checks if student with given personal number exists. Returns true if students does not exist, false otherwise  
    2.2.	addStudent(s: Student): string // adds new student to list (if student with personalNumber exists throws error), returns id of inserted student. id should be generated using https://www.npmjs.com/package/uuid  
    2.3.	removeStudent(id: string)// deletes student from list  
    2.4.	updateStudent(s: Student)// updates student, if student is not found in list, throws error  
    2.5.	getStudents(): Student[] returns all students  
    2.6.	Decide where to provide service  
3.	Create StudentSearchService  
    3.1.	filterStudents(filter: StudentFilter) filter students according to filter object, using students list from StudentsService. firstName and lastname are matched partially(contains), personalNumber is matched exactly. If no searchOptions was set prior to calling this method, default SearchOptions config object is used (injected in constructor). If enableTotalRecordsLimit is set to true, then search results are limited by top maxSearchResultItemCount records  
    3.2.	setSearchOptions(options: SearchOptions) overrides injected SearchOptions object. Each component using this service may set its own options, independently from each other. Compnents should not interfere with each other and affect search optons set by other components  
    3.3.	Decide where to provide service (root vs component)  
4.	Create student add form wih fields firstName, lastName, personal. All fields are required. 
Add async validator for personalnumber fields (check does not exist already) using StudentServices’ validatePersonalNumber method
When submitted should call students service addStudent method.  
5.	 Create Student list component that will display students list as table, and delete button in each row. Component should get students from students service via getStudents method  
6.	Implement delete functionality using Student Service deleteStudent method  
7.	Add Quick Student search component with personal number fields and buttons: search and reset.  
    7.1.	Use studentSearchService for implementing search. Set search options to limit max results to 5  
8.	Add Advanced Student search component with fields firstName, lastName, personalNumebr and buttons: search and reset.   
    8.1.	Use studentSearchService for implementing search. Set search options to limit max results to 10  

