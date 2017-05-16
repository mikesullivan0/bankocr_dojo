# bankocr_dojo
-  Welcome to this code dojo!
- The aim is to have fun, work with different people, and explore different approaches to a challenge over the next couple of hours
- You can use whatever language your team decides
- You will not be required to submit the code

### Layout
- 15 minute setup and introduction (refreshments will be available)
- 1 hour 30 mins coding, ask questions, explore different techniques and try to meet the milestones
- 15 minute wash up, discuss different approaches and demos

### Challenge
- Write an OCR program to process bank account numbers

### User Story 1
User Story 1

You work for a bank, which has recently purchased an ingenious machine to assist in reading letters and faxes sent in by branch offices. The machine scans the paper documents, and produces a file with a number of entries which each look like this:
'''
    _  _     _  _  _  _  _
  | _| _||_||_ |_   ||_||_|
  ||_  _|  | _||_|  ||_| _| 
'''

Each entry is 4 lines long, and each line has 27 characters. The first 3 lines of each entry contain an account number written using pipes and underscores, and the fourth line is blank. Each account number should have 9 digits, all of which should be in the range 0-9. A normal file contains around 500 entries.

Your first task is to write a program that can take this file and parse it into actual account numbers.



### User Story 2

Having done that, you quickly realize that the ingenious machine is not in fact infallible. Sometimes it goes wrong in its scanning. The next step therefore is to validate that the numbers you read are in fact valid account numbers. A valid account number has a valid checksum. This can be calculated as follows:

'''
account number:  3  4  5  8  8  2  8  6  5
position names:  d9 d8 d7 d6 d5 d4 d3 d2 d1
'''

checksum calculation:
(d1+2*d2+3*d3 +..+9*d9) mod 11 = 0
So now you should also write some code that calculates the checksum for a given number, and identifies if it is a valid account number.

### User Story 3

Your boss is keen to see your results. He asks you to write out a file of your findings, one for each input file, in this format:

'''
457508000
664371495 ERR
86110??36 ILL
'''

ie the file has one account number per row. If some characters are illegible, they are replaced by a ?. In the case of a wrong checksum, or illegible number, this is noted in a second column indicating status.

### User Story 4

It turns out that often when a number comes back as ERR or ILL it is because the scanner has failed to pick up on one pipe or underscore for one of the figures. For example
'''
    _  _  _  _  _  _     _ 
|_||_|| || ||_   |  |  ||_ 
  | _||_||_||_|  |  |  | _| 

'''
The 9 could be an 8 if the scanner had missed one |. Or the 0 could be an 8. Or the 1 could be a 7. The 5 could be a 9 or 6. So your next task is to look at numbers that have come back as ERR or ILL, and try to guess what they should be, by adding or removing just one pipe or underscore. If there is only one possible number with a valid checksum, then use that. If there are several options, the status should be AMB. If you still can�t work out what it should be, the status should be reported ILL.



### Data sources
- Text files containing bank account numbers are found in this repository
- One file per user story

