<h3>Documentation for OverTheWire Bandit</h3>
<br>

**Level 0** <br>

-  Opened terminal application
-  `ssh bandit.labs.overthewire.org -p 2220 -l bandit0`
-  Got prompted by "Authenticity of host" typed: `yes`
-  Enterd password: `bandit0`

**Level 0-1** <br>

- `ls`
- `cat readme`
- retrieved password for bandit1 (boJ9jbbUNNfktd78OOpsqOltutMc3MY1)

**Level 1-2** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit1` and enter password
- `ls`
- `cat -` regular cat doesnt work so I try parenthesis
- `cat '-'` since this wont work, I remebered for executing files I use ./ to designated a file in this path
- `cat ./-`
- retrieved password for bandit2 (CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9)

**Level 2-3** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit2` and enter password
- `ls`
- Now the parenthesis mehtod will work `cat 'spaces in this filename`
- retrieved password for bandit3 (UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK)

**Level 3-4** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit3` and enter password
- `ls`
- `cd inhere/`
- `ls` doesnt display anything
- `find` command was given and it displays the name of the file without any extra arguments
- `cat ./.hidden` use the ./ from level 1
- retrieved password for bandit4 (pIwrPrtPN36QITSp3EQaw936yaFoFgAB)

**Level 4-5** <br>

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

**Level 5-6** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit5` and enter password
- `ls`
- `cd inhere/`
- `ls`
- I use the find commmand from before but use --help to find which command allows me to search a file by size `find --help`
- `find -size 1033c`
- `cat ./maybehere07/.file2`
- retrieved password for bandit6 (DXjZPULLxYr17uwoI01bNLQbtFemEgo7)

**Level 6-7** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit6` and enter password
- `ls`
- try the same command I just learned from 5 `find -size 33c`
- `find -user bandit7 -size 33c` It wont find anything here so I move directories
- `cd /`
- `find -user bandit7 -size 33c` Found it in the return output
- `cat /var/lib/dpkg/info/bandit7.password`
- retrieved password for bandit7 (HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs)

**Level 7-8** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit7` and enter password
- `ls`
- `grep millionth data.txt` I used basic grep command's before so this was an easy to figure out.
- retrieved password for bandit8 (cvX2JJa4CFALtqS87jk27qwqGhBM9plV)

**Level 8-9** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit8` and enter password
- `ls`
- trying to see if grep will work with sort `grep data.txt | sort -u`
- trying to see how sort works`sort --help`
- trying out commands`sort -u -c data.txt`
- Using uniq from the given commands `uniq --help`
- finding I need to use uniq `uniq data.txt`
- `sort data.txt | uniq -u`
- retrieved password for bandit9 (UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR)

**Level 9-10** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit9` and enter password
- using previous grep command `grep '=====' data.txt`
- `grep /=== data.txt`
- `grep -E /e `
- trying to extract only readable text`sort data.txt | grep ASCII`
- figuring out after consulting bash wiki strings can accomblish what I need `strings --data data.txt`
- retireve password for bandit10 (truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk)

**Level 10-11** <br>

- `ssh bandit.labs.overthewire.org -p 2220 -l bandit10` and enter password
- figured this command will work here based from the given commands `base64 --help`
- `base64 -d data.txt`
- retireve password for bandit11 (IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR)

**Level 11-12** <br>
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit11` and enter password
- `tr --help` seeing how to set up the command again
- using cat to extract text and then tr to rotate it correctly `cat data.txt | tr '[a-z] '[n-za-m]' | tr '[A-Z]' '[N-ZA-M]'`
- had it the wrong way around the first time `cat data.txt | tr '[n-za-m]' '[a-z]' | tr '[N-ZA-M]' '[A-Z]'`
- retrieve password for bandit12 (5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu)

**Level 12-13** <br>
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit12` and enter password
- `mkdir /tmp/daniel` create temp folder from instruction
- `cp data.txt /tmp/daniel` move the text file in here
- `cd /tmp/work`
- `mv data.txt data.gz` parsing the file into compressed form
- read wiki about hex dump and xxd wiki, also recieved help from eric because after wiki I was still unsure exactly what to do
- `xxd -r data.gz > data.txt` 
- same process as pasring back again `mv data.txt data.gz`
- rea gzip bzip2recover wiki and help
- `gunzip data.gz`
- `mv data.txt data.gz`
- `bzip2recover data.gz`
- `bunzip2 rec00001data.gz`
- reapeated again for another level of compression
- `mv rec00001data.gz data.tar.gz`
- `tar -xf data.tar.gz`
- `chmode 777 data8.bin` gives permission to use file
- `mv data8.bin data.gz` move the raw data to compressed folder
- `gunzip data.gz`
- `cat data` to retireve the final password
- retrieve password for bandit13 (8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL)

**Level 13-14** <br>
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit13` and enter password
- `ls`
- `cat sshkey.private` retrieve the private ssh key
- Safeing the key on my private machine as a .private file and moving it into the .ssh folder

**Level 14-15** <br>
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit14 -i sshkey.private` useing the private key as password
- `cat /etc/bandit_pass/bandit14` to retrieve the password needed
- `nc --help` so what arguments I need
- `nc localhost 300000` then paste the password `4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e`
- retrieve password for bandit15 (BfMYroe26WYalil77FoDi9qh59eK5xNr)

**Level 15-16** <br>
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit15` and enter password
- `nc localhost 30001` doesnt return anything
- reading the supplied openssh material shows s_client command
- `openssl s_client -connect localhost:30001` paste the previous password
- retrieve password for bandit16 (cluFn7wTiGryunymYOu4RcffSxQluehd)

**Level 16-17** <br>
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit16` and enter password
- `nmap --help` looking which arguments i need for port scan
- `nmap localhost -p31000-32000` scan found 5 open ports
- `openssl s_client -connect localhost:31046`
- `openssl s_client -connect localhost:31046`
- `openssl s_client -connect localhost:31046`
- `openssl s_client -connect localhost:31046` 4th one accpted the password
- retrieve ssh private key for bandit17

**Level 17-18** <br>
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit17 -i sshkey.private` useing the private key as password
- `ls`
- `diff passwords.new passwords.old` this gives you 2 lines, one of which is the password
- retrieve password for bandit18 (kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd)

**Level 18-19** <br>
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit18` and enter password
- consulting ssh wiki, which says you can include commands in your ssh argument at the end
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit18 "cat readme"
- retrieve password for bandit19 (IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x)

**Level 19-20** <br>
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit19` and enter password
