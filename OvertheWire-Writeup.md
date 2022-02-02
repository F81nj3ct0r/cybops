Level 0:
  For level 0, simply bring up a terminal and type in: 
    ssh bandit.labs.overthewire.org -p 2220 -l bandit0
  When prompted for password, type in the password:
    bandit0
    
Level 1:
  Since you start in the home directory already, you simply need to type in:
    cat readme
  That produces the password:
    boJ9jbbUNNfktd78OOpsqOltutMc3MY1
  Copy that value and use it as your password to log into the next level (after exiting the current machine) with the command:
    ssh bandit.labs.overthewire.org -p 2220 -l bandit1
  Paste the password you were given from the previous level and you're in!
  
Level 2:
    You are told the filename to open in this one is called "-". However, typing in "cat -" will produce an error or no text.
    To solve this, a quick google search revealed that in order to open a file beginning with "-", you must first put the "<" symbol
    before it. So we type in:
      cat < -
    and we are given the password:
      CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
    now use the same login technique from the previous steps to log into the next machine!
    
Level 3:
    For this level, the filename contains spaces in it. To solve this, you must put the filename in qoutation marks. The command to
    type in would be:
      cat "spaces in this filename"
     You are then presented with the next password to log in with:
      UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
   
Level 4:
    For this level, you need to change directories to the "inhere" directory. This can be done by typing:
      cd inhere
    From there, you need to access the .hidden file. To find this file, type in: 
      ls -la
    This will show the file name ".hidden" to you. You can then read the file contents by typing:
      cat .hidden
    This presents us with the password for the next machine:
      pIwrPrtPN36QITSp3EQaw936yaFoFgAB
 
 Level 5:
    For this level, you are told to return to the inhere directory. To see what is in the directory, you can use the:
        ls -a
    command. There are 10 files in the directory that come up. Using the previously gained knowledge, we know that in order to
    read the files we need to type:
        cat < *filename* 
    since they all contain dashes at the beginning of the names. If you try this with "-file00" it produces giberish text.
    From there, you can use the up arrow key on your keyboard to bring up the previous command and just replace the last number with
    the number of the next file. Going through each file like this, we find that "-file07" is the only human-readable file. Opening
    that file produces the password for the next machine:
        koReBOKuIDDepwhWk7jZC0RTdopnAYKh
 
 Level 6:
    For this level, go back into the inhere directory. We are told that the file is human-readable, 1033 bytes in size, and not
    executable. To find a match to these parameters, we can type in:
        man du
    This will bring up a list of all flags that can be used with the "du" command. The ones we want to take note of are the -h, -b,
    and -a. If you type in the command:
        du -h -b -a
    you will get a lot of results, but after numerous failed "grep" attempts, I decided to go through the list and look for a file
    that had 1033 bytes in it. This led me to ./maybehere07/.file2. When I opened this file using the "cat" command, I was given:
          DXjZPULLxYr17uwoI01bNLQbtFemEgo7
    which I can use to log into the next machine.

Level 7:
    For this level, we are given specific parameters that a file has. However, the file can be anywhere on the server. So we 
    start by looking at the manual page for the "find command" by typing:
        man find
    We go through this and find the flags that we need based on the parameters we are given. This gives us the flags: -group,
    -size, and -user. To search through the entire server, we just need to put the "/*" option. The command should look like:
        find /* -group bandit6 -size 33c -user bandit7
    This outputs a lot of information about files that match. Only one of those files did not have permission denied however. That
    file was "/var/lib/dpkg/info/bandit7.password" so we cat this file and are given our password:
        HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

Level 8:
    For this level, we are given the information that the password is stored in the file data.txt next to the word "millionth".
    If we cat data.txt, there is way too much information to go through on our own, so we need to grep out the word millionth.
    To do this, we can use the command:
        cat data.txt | grep "millionth"
    This will reveal the word millionth as well as the password:
        cvX2JJa4CFALtqS87jk27qwqGhBM9plV

Level 9:
    For this, we are told that the password is the only line of text that occurs only once in a file. I initally tried the 
    command:
        cat data.txt | uniq -u
    but this did not work and printed the whole document out. So, I went back through the uniq manual. I then went through the 
    manuals of all other listed programs and found that I could use the sort command in conjunction with the uniq command by typing:
        sort data.txt | uniq -u
    This then produced the password:
        UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

Level 10:
    For this challenge, you have to filter out all the non-human readable characters from the file and get the password which 
    comes after multiple = signs. To do this, you can use the strings command and look for the human readable outputs by typing:
        strings --data data.txt
    this produces an output after multiple = signs that can be read to say "the password is:
        truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

Level 11:
    For this one, you just have to decode the base64 document. This can be done by typing:
        base64 -d data.txt
    This gives you the password:
        IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

Level 12:
    For this level, you need to shift all of the characters back 13 spaces (AKA a rot13 cipher). I was able to look up a simple ROT
    13 cipher script on google and it came up with:
        echo "Your text here" | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'
    so if you cat the file and copy the output, then put that output into this command, like this:
        echo "Gur cnffjbeq vf 5Gr8L4qetPEsPk8htqjhRK8XSP6x2RHh" | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'
    you will get the output:
        The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

Level 13:
    This level takes a lot of commands, for simplicity’s sake, I have just listed them in order here:
        mkdir /tmp/work
        cp data.txt /tmp/work
        cd /tmp/work
        mv data.txt data.gz
        xxd –r data.gz > data.txt
        mv data.txt data.gz
        gunzip data.gz
        mv data data.gz
        bzip2recover data.gz
        bunzip2 rec00001data.gz.bz2
        gunzip rec00001data.gz
        mv rec00001data data.gz
        bzip2recover data.gz
        bunzip2 rec00001data.gz.bz2
        mv rec00001data.gz data.tar.gz
        tar -xf data.tar.gz
        chmod 777 data8.bin
        mv data8.bin data.gz
        gunzip data.gz
        cat data
    After this whole process, the file should say:
       The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL

Level 14:
    For this level, you are given a private ssh key that can be used to log into the next level instead of a password.
    To solve this, you must first type 
        cat sshkey.private file
    Then, copy this output and save it to a text file on your local machine's desktop or location of choice
    Once you have it saved as a .txt file, save it instead as a file called (With .private being the file extension):
        sshkey.private
    Then, open a new terminal window, and "cd" into the directory that you saved the file in.
    Once there, type the command:
        ssh bandit.labs.overthewire.org -p 2220 -l bandit14 -i sshkey.private
    And you are in! 
    
Level 15:
    For this level, you just need to log into the next level using the password in the previously given location by typing:
        cat /etc/bandit_pass/bandit14
    This produces the password:
        4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
    From there, you can type in the command:
        nc localhost 30000
    Then immidiately paste the password from before and hit enter.
    You are given the new password:
        BfMYroe26WYalil77FoDi9qh59eK5xNr

Level 16:
    For this level, you must use the password of the current level and openssl
    After looking at openssl's man page, you can see that you need to use the s_client -connect command. Do this by typing:
        openssl s_client -connect localhost:30001
    Paste the password for this machine (BfMYroe26WYalil77FoDi9qh59eK5xNr) and you are given the new password:
        cluFn7wTiGryunymYOu4RcffSxQluehd

Level 17:
    For this level you must use nmap to find the port running ssl to get into the next machine by typing:
        nmap -sV localhost -p 31000-32000
    This will show you 2 ports running ssl in that range: 31518 and 31790
    We can see from the output of the nmap scan that port 31790 has a password needed to get in. We will try logging into this one using the command:
        openssl s_client -connect localhost:31790
    Then paste the password from the current level (cluFn7wTiGryunymYOu4RcffSxQluehd) and you get the private key of the new level.
    Then, copy this private key and save it to a text file on your local machine's desktop or location of choice
    Once you have it saved as a .txt file, save it instead as a file called (With .private being the file extension):
        key2.private
    Then, open a new terminal window, and "cd" into the directory that you saved the file in.
    Once there, type the command:
        ssh bandit.labs.overthewire.org -p 2220 -l bandit17 -i key2.private
    And you are in!

Level 18:
    For this level, you need to find the difference between the 2 files. This can be done with the command:
        diff passwords.old passwords.new
    This presents you with 2 passwords as output: 
        w0Yfolrc5bwjS4qw5mq1nnQi6mF03bii
                      And
        kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
    The second password is the correct one and you can use it to log into the next level.

Level 19:
    Since someone has logged in and made it kick you off when you log on, you must retrieve the password before it kicks you off. This can be done by opening a new terminal and typing the command:
        ssh bandit.labs.overthewire.org -p 2220 -l bandit18 "cat readme"
    And entering the password from the previous level. This shows you the new password:
        IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x


