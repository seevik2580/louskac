# louskac.py
ethereum wallet recovery password multithread tool, baked from [pyethrecover](https://github.com/burjorjee/pyethrecover) and [pyethereum](https://github.com/ethereum/pyethereum), for using keystore v3 json file to help recover your lost password if you know some phrases using both brute and wordlist technique, start + end words, whole ascii or just numbers

## Video demonstration
[https://www.youtube.com/watch?v=BFvTJP32dxA](https://www.youtube.com/watch?v=BFvTJP32dxA)

## requirements:
- Linux / Windows 10 Anniversary Update or newer and Windows Subsystem for Linux enabled.
- python 2.7.x
 
## dependency install:
`sudo apt-get install python-pip python-dev libssl-dev build-essential automake pkg-config libtool libffi-dev libgmp-dev`

## python modules requirements:
-`sudo apt-get install pandoc`
-`sudo pip install setuptools --upgrade`
-`sudo pip install joblib`
-`sudo pip install pypandoc`
-`sudo pip install markdown`
-`sudo pip install rlp==0.6.0`
-`sudo pip install ethereum==2.1.5`

## usage:
every print and option in czech language, maybe in future i will translate it to english.

1. `python generuj.py -h` #wordlist generator
    - -h                # help
    - -s any,words      # comma separated words
    - -v file           # words from file separated by comma
    - -a                # generate from ascii table
    - -min number       # specify minimal generated word lenght
    - -max number       # specify maximal generated word lenght
    
2. `python louskac.py`  #eth wallet password tester
    - -h                # help
    - -p file           # keystore ethereum wallet file
    - -z file           # starting words separated by line
    - -k file           # ending words separated by line
    - -v N              # number of threads of jobs
    - -w file           # wordlist file
    - -b arg            # bruteforce type
        - ASCII         # whole ascii table
        - whatever char by char eg. 1234567890 or @#!$%^&*(
    - -d N              # bruteforce character leght

### uploaded test dummy wallet for test purposes, password:
# theAnswerToLifeUniverseAndEverythingIs42

### examples generuj.py:
  #### makes all possible combinations of words separated by comma. 
  `python generuj.py -s "fist,second,third"`      
  
  #### makes all possible combinations of words inside file input.txt separated by comma.
  `python generuj.py -v input.txt`                
  
  #### makes all possible combinations of numbers 1,2,3,4,5,6,7,8,9,0 with minimal lenght 8. less lenght size is skipped.
  `python generuj.py -min 8 -s "1,2,3,4,5,6,7,8,9,0"`

  #### makes all possible combinations of numbers 1,2,3,4,5,6,7,8,9,0 with maximal lenght 4, more lenght size is skipped.
  `python generuj.py -max 4 -s "1,2,3,4,5,6,7,8,9,0"`

  - generated wordlist will be in same directory with name wordlist_01.txt. 
  - When wordlist reach maximum file size 50MB then new file will be created with next name wordlist_02.txt

### examples louskac.py:
  #### bruteforce numbers from 0 to 9 with size of 2
  `python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -b 1234567890 -d 2`
  
  #### bruteforce @#! with size of 3
  `python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -b @#! -d 3`
  
  #### bruteforce whole ASCII table with size of 4 
  `python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -b ASCII -d 4`
  
  #### bruteforce numbers from 0 to 9 with size of 2 and starting words from file start.txt separated by lines
  `python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -b 1234567890 -d 2 -z start.txt`
  
  #### bruteforce numbers from 0 to 9 with size of 4 and ending words from file end.txt separated by lines
  `python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -b 1234567890 -d 2 -k end.txt`
  
  #### use words from wordlist generated by generuj.py
  `python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -w wordlist_01.txt`
  
  #### use starting words from file start.txt and words from wordlist generated by generuj.py
  `python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -z start.txt -w wordlist_01.txt`
  
  #### use words from wordlist generated by generuj.py and ending words from file end.txt
  `python louskac.py -p UTC--2017-07-12T00-06-42.772050600Z--f5751c906091b98be2a6be5ce42c573d704aedab -w wordlist.txt -k end.txt`
  
  # donate 
  - ETH 0x9ead6a02058d461d8f7d09403c22cc278148ddfc
  - ZEC t1bVtZEM8rF5N9JY2fHNULQaaJU9LHwTCB5
  - BTC 3BWxLUPQCWFdwKmVZYk88zX2hajdP5ZXxF
