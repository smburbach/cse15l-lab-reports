# Lab Report 3

Sarah Burbach

**find -type _**

* The -type operator of the find command will find the 'type' provided in the command line arugment. There are many 'types' that you can provide this command including 'f' to indicate files and 'd' to indicate directories

*Example 1:* In the following command I ran the find command on the technical directory, with the operator -type d. This command finds and prints all of the directories inside the technical directory. This is useful for getting a list of all the directories in a given directory. This would be especially useful in a large file set that you are not familiar with. 

```
sarahburbach@Sarahs-Air docsearch % find technical -type d
technical
technical/government
technical/government/About_LSC
technical/government/Env_Prot_Agen
technical/government/Alcohol_Problems
technical/government/Gen_Account_Office
technical/government/Post_Rate_Comm
technical/government/Media
technical/plos
technical/biomed
technical/911report
```

*Example 2:* I used -type d command on technical/government. You can see the difference from the previous command and this one -- this one only prints the directories within government, rather than all of the directorites in technical. Again, similar to example 2, this is useful for getting an overview of all the directories in a certain path. 

```
sarahburbach@Sarahs-Air docsearch % find technical/government -type d
technical/government
technical/government/About_LSC
technical/government/Env_Prot_Agen
technical/government/Alcohol_Problems
technical/government/Gen_Account_Office
technical/government/Post_Rate_Comm
technical/government/Media
```

*Example 3:* I used -type f, inside the technical/government/Post_Rate_Comm. The 'f' argument tells the find command to file all of the objects that are files. You can see that it prints the names of all of the files inside this directory. This is useful for geting a list of all the files in a specific directory and, when combined with other find operators, could be very useful get getting a list of only files that match a specific set of requirements. 

```
sarahburbach@Sarahs-Air docsearch % find technical/government/Post_Rate_Comm -type f
technical/government/Post_Rate_Comm/Gleiman_EMASpeech.txt
technical/government/Post_Rate_Comm/Mitchell_spyros-first-class.txt
technical/government/Post_Rate_Comm/Cohenetal_CreamSkimming.txt
technical/government/Post_Rate_Comm/Cohenetal_DeliveryCost.txt
technical/government/Post_Rate_Comm/Mitchell_RMVancouver.txt
technical/government/Post_Rate_Comm/Gleiman_gca2000.txt
technical/government/Post_Rate_Comm/Cohenetal_Cost_Function.txt
technical/government/Post_Rate_Comm/Redacted_Study.txt
technical/government/Post_Rate_Comm/Mitchell_6-17-Mit.txt
technical/government/Post_Rate_Comm/Cohenetal_comparison.txt
technical/government/Post_Rate_Comm/Cohenetal_Scale.txt
technical/government/Post_Rate_Comm/Cohenetal_RuralDelivery.txt
technical/government/Post_Rate_Comm/ReportToCongress2002WEB.txt
technical/government/Post_Rate_Comm/WolakSpeech_usps.txt
```

**find -or**

* This command allows you to combine two other find commands (such as type or name) to search for files/directories that matches at least one of the statements.

*Example 1:* In this example, I used the -or operator to combine the -name and -type d operators, to find objects that are either a directory or have a name that matches "chapter-1*.txt". This is useful to find objects that match at least one requirement. 

```
sarahburbach@Sarahs-Air docsearch % find technical -name "chapter-1*.txt" -or -type d
technical
technical/government
technical/government/About_LSC
technical/government/Env_Prot_Agen
technical/government/Alcohol_Problems
technical/government/Gen_Account_Office
technical/government/Post_Rate_Comm
technical/government/Media
technical/plos
technical/biomed
technical/911report
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-1.txt
technical/911report/chapter-12.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
```

*Example 2:* In this example, I again used the -or operator to combine the -type d and -name operators, but this time I did so in the technical/goverment directory rather than all of technical. Similar to the first example, this is useful for finding a list of objects that match at least one set of criteria and this specific example shows that you can use also use this command in any path/directory that you can use find in. 

```
sarahburbach@Sarahs-Air docsearch % find technical/government -type d -or -name "Session*.txt"
technical/government
technical/government/About_LSC
technical/government/Env_Prot_Agen
technical/government/Alcohol_Problems
technical/government/Alcohol_Problems/Session2-PDF.txt
technical/government/Alcohol_Problems/Session3-PDF.txt
technical/government/Alcohol_Problems/Session4-PDF.txt
technical/government/Gen_Account_Office
technical/government/Post_Rate_Comm
technical/government/Media
```

*Example 3:* In this example, I used -or to combine two -name commands, with different string requirements. This allowed me to get a list of txt files that matched one of two different strings (rather than just one), which is useful if you are looking for files that match different string patterns. 

```
sarahburbach@Sarahs-Air docsearch % find technical -name "chapter-1*.txt" -or -name "journal*1.txt"
technical/plos/journal.pbio.0020431.txt
technical/plos/journal.pbio.0030021.txt
technical/plos/journal.pbio.0030051.txt
technical/plos/journal.pbio.0030131.txt
technical/plos/journal.pbio.0020121.txt
technical/plos/journal.pbio.0020241.txt
technical/plos/journal.pbio.0020101.txt
technical/plos/journal.pbio.0020311.txt
technical/plos/journal.pbio.0020071.txt
technical/plos/journal.pbio.0020001.txt
technical/plos/journal.pbio.0020161.txt
technical/plos/journal.pbio.0020401.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-1.txt
technical/911report/chapter-12.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
```

**find -maxdepth**

* The -maxdepth operator allows you set set a max 'level' that you want the find command to search in. This level is determined by the number you provide after the operator. 


*Example 1:* In this example I set the maxdepth to one, such that it only searches in the given directory (technical) and the next directories. This is useful to limit the scope of your search from the opposite direction that the path allows you to.  

```
sarahburbach@Sarahs-Air docsearch % find technical -type d -maxdepth 1
technical
technical/government
technical/plos
technical/biomed
technical/911report
```

*Example 2:* In this example, I ran the same command as example 2 but changed the maxdepth to 2 -- you can see that this adds a third level of directories (those inside the government directory). This would be especially useful in file structures with many directories and files, becuase it would allow you to pinpoint exactly what directories you want to be searched. 

```
sarahburbach@Sarahs-Air docsearch % find technical -type d -maxdepth 2
technical
technical/government
technical/government/About_LSC
technical/government/Env_Prot_Agen
technical/government/Alcohol_Problems
technical/government/Gen_Account_Office
technical/government/Post_Rate_Comm
technical/government/Media
technical/plos
technical/biomed
technical/911report
```

*Example 3:* In this example, I combined the maxdepth command with the -name command inside the path technical/biomed to find the text files. This is useful becuase, using by combining the limits of the path and the maxdepth command, it allowed me to search for files in one specific directory (biomed).

```
sarahburbach@Sarahs-Air docsearch % find technical/biomed -name "*14.txt" -maxdepth 2
technical/biomed/1475-2875-2-14.txt
technical/biomed/1471-2148-2-14.txt
technical/biomed/gb-2001-2-4-research0014.txt
technical/biomed/gb-2003-4-2-r14.txt
technical/biomed/1471-2105-3-14.txt
technical/biomed/1471-2202-2-14.txt
technical/biomed/1471-2148-1-14.txt
technical/biomed/1471-2210-2-14.txt
technical/biomed/1471-2164-4-14.txt
technical/biomed/1471-2091-3-14.txt
technical/biomed/1472-6750-2-14.txt
technical/biomed/1472-6963-3-14.txt
technical/biomed/1475-2875-1-14.txt
technical/biomed/1471-2407-3-14.txt
technical/biomed/1471-2202-3-14.txt
```

Source:
* https://math2001.github.io/article/bashs-find-command/