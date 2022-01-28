<h3>Documentation for OverTheWire Bandit</h3>
<br>

//less doc style, more human read style of me explaining what i did and how   / if learned new command, denote

**Setup** <br>

1.  Opened terminal application
2.  `ssh bandit.labs.overthewire.org -p 2220 -l bandit0`
3.  Got prompted by "Authenticity of host" typed: `yes`
4.  Enterd password: `bandit0`

**Level 0** <br>

1. `ls`
2. `cat readme`
3. retrieved password for bandit1 (boJ9jbbUNNfktd78OOpsqOltutMc3MY1)

**Level 1** <br>

1. `ssh bandit.labs.overthewire.org -p 2220 -l bandit1` and enter password
2. `ls`
3. `cat -`
4. `cat '-'`
5. `cat ./-`
6. retrieved password for bandit2 (CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9)

**Level 2** <br>

1. `ssh bandit.labs.overthewire.org -p 2220 -l bandit2` and enter password
2. `ls`
3. `cat 'spaces in this filename`
4. retrieved password for bandit3 (UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK)

**Level 3** <br>

1. `ssh bandit.labs.overthewire.org -p 2220 -l bandit3` and enter password
2. `ls`
3. `cd inhere/`
4. `ls`
5. `find`
6. `cat ./.hidden`
7. retrieved password for bandit4 (pIwrPrtPN36QITSp3EQaw936yaFoFgAB)

**Level 4** <br>

1. `ssh bandit.labs.overthewire.org -p 2220 -l bandit4` and enter password
2. `ls`
3. `cd inhere/`
4. `cat ./-file00`
5. `cat ./-file01`
6. `cat ./-file02`
7. `cat ./-file03`
8. `cat ./-file04`
9. `cat ./-file05`
10. `cat ./-file06`
11. `cat ./-file07`
12. retrieved password for bandit5 (koReBOKuIDDepwhWk7jZC0RTdopnAYKh)

**Level 5** <br>

1. `ssh bandit.labs.overthewire.org -p 2220 -l bandit5` and enter password
2. `ls`
3. `cd inhere/`
4. `ls`
5. `find --help`
6. `find -size 1033c`
7. `cat ./maybehere07/.file2`
8. retrieved password for bandit6 (DXjZPULLxYr17uwoI01bNLQbtFemEgo7)

**Level 6** <br>

1. `ssh bandit.labs.overthewire.org -p 2220 -l bandit6` and enter password
2. `ls`
3. `find -size 33c`
4. `find -user bandit7 -size 33c`
5. `cd /`
6. `find -user bandit7 -size 33c`
7. `cat /var/lib/dpkg/info/bandit7.password`
8. retrieved password for bandit7 (HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs)

**Level 7** <br>

1. `ssh bandit.labs.overthewire.org -p 2220 -l bandit7` and enter password
2. `ls`
3. `grep millionth data.txt`
4. retrieved password for bandit8 (cvX2JJa4CFALtqS87jk27qwqGhBM9plV)

**Level 8** <br>

1. `ssh bandit.labs.overthewire.org -p 2220 -l bandit8` and enter password
2. `ls`
3. `grep -E '(.)(.*\)' data.txt`
4. `grep data.txt | sort -u`
5. `sort -u`
6. `sort -u -c data.txt`
7. `uniq data.txt`
8. `sort data.txt | uniq -u`
9. retrieved password for bandit9 (UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR)

**Level 9** <br>

1. `ssh bandit.labs.overthewire.org -p 2220 -l bandit9` and enter password
2. `grep '=====' data.txt`
3. `grep /=== data.txt`
4. `grep -E /e `
5. `sort data.txt | grep ASCII`
6. `strings --data data.txt`
7. retireve password for bandit10 (truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk)

**Level 10** <br>

1. `ssh bandit.labs.overthewire.org -p 2220 -l bandit10` and enter password
2. `base64 -d data.txt`
3. retireve password for bandit11 (IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR)

**Level 11** <br>

1. `ssh bandit.labs.overthewire.org -p 2220 -l bandit11` and enter password
2. `cat data.txt | tr '[a-z] '[n-za-m]' | tr '[A-Z]' '[N-ZA-M]'`
3. `cat data.txt | tr '[n-za-m]' '[a-z]' | tr '[N-ZA-M]' '[A-Z]'`
4. retrieve password for bandit12 (5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu)

**Level 12** <br>

1. `ssh bandit.labs.overthewire.org -p 2220 -l bandit12` and enter password
2. 
