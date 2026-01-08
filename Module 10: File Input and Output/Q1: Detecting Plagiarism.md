````python
import check


def preprocess_text(text):
  '''
  Returns a pre-processed string of text where all letters are lower case; 
  numbers, dashes, and slashes remain; single quotes, consecutive spaces and 
  "\n", beginning/ending whitespaces, and all other characters removed 
  
  preprocess_text: Str -> Str
  
  Examples:
    preprocess_text("This is a 'test'!\n Try with  2-4-grams.") =>
                   "this is a test try with 2-4-grams"
    preprocess_text("") => ""
    preprocess_text("Hi! My name is  'Michelle'.") => "hi my name is michelle"
  '''
  lower_case = text.lower()
  new_str = ""
  
  for pos in range(len(lower_case)):
    char = lower_case[pos]
    
    if char.isnumeric() or char == "-" or char == "/":
      new_str += char
      
    elif char == "'":
      if lower_case[pos-1].isalpha() and lower_case[pos+1].isalpha():
        new_str += char
        
    elif char.isalpha():
      new_str += char
      
    else:
      new_str += " "
     
  los = new_str.split() 
  answer = " ".join(los)
  return answer
      
    
def get_ngrams(text, n, fnameout):
  '''
  Returns a dictionary where keys are n-grams of text of length n and values are
  the number of duplicates, and writes each key-value pair in a new file,
  "fnameout.txt", in ASCII (lexicographical) order
  
  Effects:
    Writes to a file called "fnameout.txt"
  
  get_ngrams: Str Nat Str -> (dictof Str Nat) 
  Requires:
    text is pre-processed 
    n > 0 
    
  Examples:
    get_ngrams("banana", 2, "fruit.txt") => {"ba":1, "an":2, "na":2}
    and fruit.txt contains the following:
      an,2
      ba,1
      na,2
      
    get_ngrams("499296$ !", 20, "out.txt") => {}
    and out.txt will be an empty file 
    
    get_ngrams("", 1, "base.txt") => {}
    and base.txt will be an empty file 
  '''
  ngrams = {}
  
  if len(text) > n:
    for pos in range(len(text)):
      if pos <= len(text) - n:
        if text[pos:pos+n] not in ngrams:
          ngrams[text[pos:pos+n]] = 1
        else:
          ngrams[text[pos:pos+n]] += 1
          
  sorted_ngrams = sorted(ngrams.items())
    
  fout = open(fnameout, "w")
  for item in sorted_ngrams:
    fout.write(item[0] + "," + str(item[1]) + "\n")
  fout.close()
  
  return ngrams
  
  
def jaccard_ngram(d1, d2):
  '''
  Returns the jaccard similarity score between d1 and d2 
  
  jaccard_ngram: (dictof Str Nat) (dictof Str Nat) -> Float
  Requires:
    d1 and d2 keys have same length and values are positive integers 
    
  Examples:
    jaccard_ngram({"ba":1, "na":2, "an":2}, {"ba":1, "na":1, "an":1}) => 0.6
    jaccard_ngrams({}, {}) => 1.0
    jaccard_ngrams({"ab":5, "bc":2}, {"de":2, "bc":10}) => 0.11765
  '''
  union = {} 
  
  for key in d1:
    if key not in union:
      union[key] = d1[key]
      
  for key in d2:
    if key not in union:
      union[key] = d2[key]
    else:
      union[key] = max(union[key], d2[key])
  
  union_size = 0
  for key in union:
    union_size += union[key] #Above codes for size of union
  
  intersect = {} 
  d1_length = len(d1)
  d2_length = len(d2)
  shortest = ""
  longest = ""
  
  if d1_length > d2_length:
    shortest = d2
    longest = d1
  else:
    shortest = d1
    longest = d2
    
  for key in shortest:
    if key in longest:
      intersect[key] = min(shortest[key], longest[key]) 
      
  intersect_size = 0
  for key in intersect:
    intersect_size += intersect[key] #Above codes for size of intersect
    
  if union_size == 0 and intersect_size == 0:
    return 1.0
  else:
    return intersect_size / union_size


def document_similarity(filename1, filename2, n):
  '''
  Reads two files, filename1 and filename2, and returns the Jaccard multi-set
  score for the n-grams of length n extracted from the two named files 
  
  Effects:
    Reads two files named filename1 and filename2
    
  document_similarity: Str Str Nat -> Float
  Requires:
    filename1 and filename2 are valid files in the current directory 
    n > 0
    
  Examples:
    document_similarilty("ex1.txt", "ex1.txt", 3) => 1.0
    assuming ex1.txt is a file with Computer Science and \n on separate lines
    
    document_similarity("base.case.txt", "base.case.txt", 6) => 1.0
    assuming base.case.txt is an empty file 
  '''
  fin1 = open(filename1)
  fin1_lines = " ".join(fin1.readlines())
  fin1.close()
  fin2 = open(filename2)
  fin2_lines = " ".join(fin2.readlines())
  fin2.close()
  
  process_f1 = preprocess_text(fin1_lines) 
  process_f2 = preprocess_text(fin2_lines) 
  
  ngrams_f1 = get_ngrams(process_f1, n, "_dummy1.txt")
  ngrams_f2 = get_ngrams(process_f2, n, "_dummy2.txt")
  
  return jaccard_ngram(ngrams_f1, ngrams_f2)


##Examples & tests for preprocess_text
check.expect("MarkUs Basic Test",
             preprocess_text("This is a 'test'!\n Try with  2-4-grams."),
             "this is a test try with 2-4-grams")
check.expect("Base Case, Empty String", preprocess_text(""), "")
check.expect("Personal Example", 
             preprocess_text("Hi! My name is  'Michelle'."),
             "hi my name is michelle")
check.expect("No Changes", preprocess_text("hi/ t-his is un3changed"),
             "hi/ t-his is un3changed")
check.expect("All Whitespace", preprocess_text("     \n"), "")
check.expect("Apostrophes Kept", preprocess_text("Let's keep this"),
             "let's keep this")
check.expect("Remove All", preprocess_text("+!?\n  &  "), "")


##Examples & tests for get_ngrams
##markus_test_expected.txt contains an,2, ba,1, and na,2 once per line 
check.set_file_exact("markus_test_out.txt", "markus_test_expected.txt")
check.expect("MarkUs Basic Test", 
             get_ngrams("banana", 2, "markus_test_out.txt"), 
             {"ba": 1, "an": 2, "na": 2})

#out.txt_expected.txt is an empty file 
check.set_file_exact("out.txt", "out.txt_expected.txt")
check.expect("Provided Example", get_ngrams("499296$ !", 20, "out.txt"), {})

#base.txt_expected.txt is an empty file 
check.set_file_exact("base.txt", "base.txt_expected.txt")
check.expect("Base Case, Empty String & n=1", get_ngrams("", 1, "base.txt"), {})

#duplicates.txt_expected.txt contains aaa,4 once on a single line
check.set_file_exact("duplicates.txt", "duplicates.txt_expected.txt")
check.expect("All Duplicates", 
             get_ngrams("aaaaaa", 3, "duplicates.txt"), {"aaa":4})
           
             
##Examples & tests for jaccard_ngram             
check.within("MarkUs Basic Test", 
             jaccard_ngram({'ba': 1, 'na': 2, 'an': 2}, 
                           {'ba': 1, 'na': 1, 'an': 1}), 0.6, 0.00001)
check.within("Base Case, Empty Dicts", jaccard_ngram({}, {}), 1.0, 0.00001)
check.within("Personal Example", 
             jaccard_ngram({"ab":5, "bc":2}, 
                           {"de":2, "bc":10}), 0.11765, 0.00001)
check.within("100% Match", jaccard_ngram({"ab":2}, {"ab":2}), 1.0, 0.00001)
check.within("0% Match", jaccard_ngram({"ab":2}, {"bc":5}), 0.0, 0.00001)
check.within("len(d1) > len(d2)", 
             jaccard_ngram({"ab":2, "bc":2, "de":2}, 
                           {"bc":10}), 0.14286, 0.00001)
      
             
##Examples & tests for document_similarity
#ex1.txt contains Computer Science and \n once per line 
#_dummy1.txt and _dummy2.txt contains the following on separate lines:
# sc,1, cie,1, com,1, enc,1, er ,1, ien,1, mpu,1, nce,1, omp,1, put,1, r s,1,
#sci,1, ter,1, ute,1
check.within("doc sim self", 
             document_similarity("ex1.txt", "ex1.txt", 3), 1.0, 0.00001)
             
#base.case.txt is an empty file 
#_dummy1.txt and _dummy2.txt are empty files
check.within("Base Case, Both Empty Files", 
             document_similarity("base.case.txt", "base.case.txt", 6), 
             1.0, 0.00001) 
 
#ex1.txt and base.case.txt contain the same lines as specified previously
#_dummy1.txt contains the same lines as specified in the "doc sim self" test
#_dummy2.txt is an empty file 
check.within("0% Match", 
             document_similarity("ex1.txt", "base.case.txt", 3), 0.0, 0.00001)
````
