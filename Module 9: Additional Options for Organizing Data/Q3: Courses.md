````python
import check


class Course:
  ''' 
  Represents a course attempt by a particular student

  Fields: 
    code (Str)
    term (Nat)
    grade (anyof Nat Str)
			          
  Requires: 
    term is 4 digits (e.g. ths term is 1205)
    if grade is a nat, 0 <= grade <= 100
	  if grade is a str, it is one of
	  "WD", "WF", "DNW", "INC", "CR", "NCR"
  '''
	  
  def __init__(self, code, term, grade):
    self.code = code 
    self.term = term
    self.grade = grade
	  
  def __repr__(self):
    return "Course({0}, {1}, {2})".format(
              self.code, self.term, self.grade)
  
  def __eq__(self,other):
	  return isinstance(other,Course) and \
	           self.code == other.code and \
	           self.term == other.term and \
	           self.grade == other.grade
	           
def course_list_by_term(courses):
  '''
  Returns a dictionary where keys are terms covered in courses and values are
  courses the student took that term 
  
  course_list_by_term: (listof Course) -> (dictof Nat (listof Course))
  
  Examples:
    CS115 = Course("CS115", 1199, 75)
    MATH135 = Course("MATH135", 1199, 80)
    CS116a = Course("CS116", 1201, "NCR")
    MATH136 = Course("MATH136", 1201, "CR")
    CS116b = Course("CS116",1205, 80)
    example_list = [CS115, MATH135, CS116a, MATH136, CS116b]
  
    course_list_by_term(example_list) =>
      {1199:[CS115, MATH135], 1201:[CS116a, MATH136], 1205:[CS116b]}
      
    course_list_by_term([]) => {}
    
    ECON211 = Course("ECON211", 1239, 98) 
    ECON201 = Course("ECON201", 1235, 92)  
    
    course_list_by_term([ECON211, ECON201]) => {1239:[ECON211], 1235:[ECON201]}
  '''
  course_list = {}
  for course in courses:
    if course.term in course_list:
      course_list[course.term].append(course)
    else:
      course_list[course.term] = [course]
  return course_list


def term_average(courses):
  '''
  Returns a dictionary where keys are terms covered in courses and values are
  the student's average grades that term, or None if there are no valid courses
  
  term_average: (listof Course) -> (dictof Nat Float)
  
  Examples:
    CS115 = Course("CS115", 1199, 75)
    MATH135 = Course("MATH135", 1199, 80)
    CS116a = Course("CS116", 1201, "NCR")
    MATH136 = Course("MATH136", 1201, "CR")
    CS116b = Course("CS116",1205, 80)
    example_list = [CS115, MATH135, CS116a, MATH136, CS116b]
    
    term_average(example_list) => {1199:77.5, 1201:None, 1205:80.0}
    
    term_average([]) => {}
    
    ECON211 = Course("ECON211", 1239, 98) 
    ECON201 = Course("ECON201", 1235, 92) 
    
    term_average([ECON211, ECON201]) => {1239:98.0, 1235:92.0}
  '''
  term_averages = {}
  course_list = course_list_by_term(courses)
  
  for term in course_list:
    term_courses = course_list[term]
    grades = []
    
    for course in term_courses:
      if str(course.grade).isnumeric() and str(course.grade) >= "32":
        grades.append(course.grade)
      elif course.grade in ["WF", "DNW"] or str(course.grade) < "32":
        grades.append(32)
        
    if grades == []:
      term_averages[term] = None
    else:
      term_averages[term] = sum(grades) / len(grades)
    
  return term_averages     


def highest_grade(courses):
  '''
  Returns a dictionary where keys are course codes in courses and values are the
  highest numerical grades achieved in each course, or excluded if none 
  
  highest_grade: (listof Course) -> (dictof Str Nat)
  
  Examples:
    CS115 = Course("CS115", 1199, 75)
    MATH135 = Course("MATH135", 1199, 80)
    CS116a = Course("CS116", 1201, "NCR")
    MATH136 = Course("MATH136", 1201, "CR")
    CS116b = Course("CS116",1205, 80)
    example_list = [CS115, MATH135, CS116a, MATH136, CS116b]
    
    highest_grade(example_list) => {"CS115":75, "MATH135":80, "CS116":80}
    
    highest_grade([]) => {}
    
    ECON211 = Course("ECON211", 1239, 98) 
    ECON201 = Course("ECON201", 1235, 92)
    
    highest_grade([ECON211, ECON201]) => {"ECON211":98, "ECON201":92}
  '''
  grades = {}
  for course in courses:
    if str(course.grade).isnumeric():
      grades[course.code] = course.grade
    elif course.grade in ["WF", "DNW"]:
      grades[course.code] = 32
  return grades

##Constants for testing
CS115 = Course("CS115", 1199, 75)
MATH135 = Course("MATH135", 1199, 80)
CS116a = Course("CS116", 1201, "NCR")
MATH136 = Course("MATH136", 1201, "CR")
CS116b = Course("CS116",1205, 80)
example_list = [CS115, MATH135, CS116a, MATH136, CS116b]	

ECON211 = Course("ECON211", 1239, 98)
ECON201 = Course("ECON201", 1235, 92)
BIOL308 = Course("BIOL308", 1225, "WD")
BIOL450 = Course("BIOL450", 1221, "INC")
BIOL266 = Course("BIOL266", 1239, "WF")
CHEM237 = Course("CHEM237", 1225, "DNW")
CHEM266 = Course("CHEM266", 1219, 20)
BIOL273 = Course("BIOL273", 1201, 32)

##Examples & Tests for course_list_by_term
check.expect("MarkUs Basic Test 1", course_list_by_term(example_list),
	           {1199: [CS115, MATH135],
	            1201: [CS116a, MATH136],
	            1205: [CS116b]})
check.expect("Base Case, No Courses", course_list_by_term([]), {})
check.expect("Personal Example", course_list_by_term([ECON211, ECON201]),
             {1239: [ECON211], 1235: [ECON201]})
             
##Examples & Tests for term_average             
check.within("MarkUs Basic Test 2", term_average(example_list),
             {1199: 77.5, 1201: None, 1205: 80.0}, 0.00001)
check.within("Base Case, No Courses", term_average([]), {}, 0.00001)
check.within("Personal Example", term_average([ECON211, ECON201]),
             {1239: 98.0, 1235: 92.0}, 0.00001)
check.within("WD, INC", term_average([BIOL308, BIOL450]),
             {1225: None, 1221: None}, 0.00001)
check.within("WF, DNW, grade <= 32", 
             term_average([BIOL266, CHEM237, CHEM266, BIOL273]),
             {1239: 32.0, 1225: 32.0, 1219: 32.0, 1201: 32.0}, 0.00001)
check.within("All None", term_average([CS116a, MATH136, BIOL308]),
             {1201: None, 1225: None}, 0.00001)
	     
##Examples & Tests for highest_grade	   
check.expect("MarkUs Basic Test 3", highest_grade(example_list),
             {"CS115": 75,
	            "MATH135": 80,
	            "CS116": 80})
check.expect("Base Case, No Courses", highest_grade([]), {})	         
check.expect("Personal Example", highest_grade([ECON211, ECON201]),
             {"ECON211": 98, "ECON201": 92})
check.expect("grade < 32", highest_grade([CHEM266]), {"CHEM266": 20})  
check.expect("No Numerical Grades", 
             highest_grade([CS116a, MATH136, BIOL308]), {})
````
