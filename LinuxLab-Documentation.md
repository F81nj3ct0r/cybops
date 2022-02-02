<h3>Documentation for OverTheWire Bandit</h3>
<br>

**Setup** <br>

-  Opened terminal application
-  `ssh bandit.labs.overthewire.org -p 2220 -l bandit0`
-  Got prompted by "Authenticity of host" typed: `yes`
-  Enterd password: `bandit0`

**Level 0** <br>

- `ls`
- `cat readme`
- retrieved password for bandit1 (boJ9jbbUNNfktd78OOpsqOltutMc3MY1)

**Level 1** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit1` and enter password
- `ls`
- `cat -` regular cat doesnt work so I try parenthesis
- `cat '-'` since this wont work, I remebered for executing files I use ./ to designated a file in this path
- `cat ./-`
- retrieved password for bandit2 (CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9)

**Level 2** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit2` and enter password
- `ls`
- Now the parenthesis mehtod will work `cat 'spaces in this filename`
- retrieved password for bandit3 (UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK)

**Level 3** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit3` and enter password
- `ls`
- `cd inhere/`
- `ls` doesnt display anything
- `find` display the name without any extra arguments
- `cat ./.hidden` use the ./ from level 1
- retrieved password for bandit4 (pIwrPrtPN36QITSp3EQaw936yaFoFgAB)

**Level 4** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit4` and enter password
- `ls`
- `cd inhere/`
- I move to the folder and just try each file till I find it.
- `cat ./-file00`
- `cat ./-file01`
- `cat ./-file02`
- `cat ./-file03`
- `cat ./-file04`
- `cat ./-file05`
- `cat ./-file06`
- `cat ./-file07`
- retrieved password for bandit5 (koReBOKuIDDepwhWk7jZC0RTdopnAYKh)

**Level 5** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit5` and enter password
- `ls`
- `cd inhere/`
- `ls`
- I never used find before so I used --help to find which command allows me to search a file by size `find --help`
- `find -size 1033c`
- `cat ./maybehere07/.file2`
- retrieved password for bandit6 (DXjZPULLxYr17uwoI01bNLQbtFemEgo7)

**Level 6** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit6` and enter password
- `ls`
- try the same command I just learned from 5 `find -size 33c`
- `find -user bandit7 -size 33c` It wont find anything here so I move directories
- `cd /`
- `find -user bandit7 -size 33c` Found it in the return output
- `cat /var/lib/dpkg/info/bandit7.password`
- retrieved password for bandit7 (HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs)

**Level 7** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit7` and enter password
- `ls`
- `grep millionth data.txt` If used basic grep command before so this was an easy given
- retrieved password for bandit8 (cvX2JJa4CFALtqS87jk27qwqGhBM9plV)

**Level 8** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit8` and enter password
- `ls`
- trying to see if grep will work with sort `grep data.txt | sort -u`
- trying to see how sort works`sort --help`
- trying out commands`sort -u -c data.txt`
- finding I need to use uniq `uniq data.txt`
- `sort data.txt | uniq -u`
- retrieved password for bandit9 (UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR)

**Level 9** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit9` and enter password
- using previous grep command `grep '=====' data.txt`
- `grep /=== data.txt`
- `grep -E /e `
- trying to extract only readable text`sort data.txt | grep ASCII`
- figuring out after consulting bash wiki strings can accomblish what I need `strings --data data.txt`
- retireve password for bandit10 (truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk)

**Level 10** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit10` and enter password
- figured this command will work here based from the given commands `base64 --help`
- `base64 -d data.txt`
- retireve password for bandit11 (IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR)

**Level 11** <br>
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit11` and enter password
- `tr --help` seeing how to set up the command again
- using cat to extract text and then tr to rotate it correctly `cat data.txt | tr '[a-z] '[n-za-m]' | tr '[A-Z]' '[N-ZA-M]'`
- had it the wrong way around the first time `cat data.txt | tr '[n-za-m]' '[a-z]' | tr '[N-ZA-M]' '[A-Z]'`
- retrieve password for bandit12 (5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu)

**Level 12** <br>
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit12` and enter password
- 
