Assume you are given a corpus of documents and your task is to extract person names and titles from this corpus. You write a program to recognize these. The program can be run many times, and each time it will leverage the names and titles recognized in previous runs to find more occurrences of names and titles. To start with you are given a list of first names, last names and titles. For simplicity, we shall assume that these lists are disjoint.

HW5 (Parts 1 and 2 and 3) 
=============
###### Part1: 
Write JAPE rules to recognize person names of the form <first_name last_name>, <last_name>, <first_name> (e.g. Bill Clinton or Clinton or Bill). Your rules must create a PersonName annotation which has two features: "first_name", "last_name". If one of the names if not present then the corresponding feature can be set to null or the annotation doesn't have to have the corresponding feature (your choice).

###### Part2:
Write JAPE rules to use the list of titles to recognize new names. The basic intuition is that if an occurrence of a title is followed by a token or a consecutive list of tokens (in the same sentence) which starts with an upper case initial then that is probably a name. E.g. "Professor Shekhar Pradhan is teaching NLP."

The JAPE rule should create an annotation PersonName, which has a "title" feature. It should also have "first_name" and a "last_name" features. In case there is title followed by only one name (e.g. "Professor Shekhar is teaching NLP"), assume that it is a last anme. Your JAPE rules should save the newly recognized first names (last anems) to a file.

###### Part3:
Expand your given list of titles to recognize new titles. Basic intuition is that a token (or a list of consecutive tokens) is a title if it immediately precedes the occurrence of a person name. Note that titles should also start with an upper case letter. But watch out for cases where the token preceding an occurrence of a name is the first word in the sentence. That can produce false positive. E.g., in "Congratulate Shekhar Pradhan", "Congratulate" is not a title.

So your rules should be cautious and not count such cases as occurrence of a title even if in fact it turns out to be a title (e.g. "Major Tom, take your protein pills"). Of course, if it is in your given list of titles it should be counted as title, regradless of whether it occurs as the first word of a sentence or not.

The names to be used in this part of the homework should be the names you were initially given augmented with the new names you recognized in Part 2.


IMPORTANT NOTE BEFORE RUN THE PROGRAM
=============

Make sure there is an empty line at the end of the files first_name.lst, last_name.lst and title.lst so that the jape script could write the new item into files correctly.

Absolute path was used in person_new_name.jape and person_new_title.jape. Change 'basePath' before run the scripts.

Run person_name.jape for question Part 1; run person_new_name.jape for Part2; run person_part3_main.jape for Part 3.

DEFAUTL TEST DATA
=============

first_name.lst
--------------
Jonny

(leave this line empty)

last_name.lst
-------------
Evans

(leave this line empty)

title.lst
---------
Sir
President
Prof.
Miss

(leave this line empty)
