**Grep** - Global regular exprression print
- searches for an expression and prints results

Print line number of value
- Grep -n "boo" grep.txt

PRint opposite of expresson
- grep -v "boo" grep.txt

only match string
- grep -o "BOO" grep.txt

Print filenames with expression
- grep -l "boo" *

ignore case
- grep -i "BOO" grep.txt

Exact matches
- grep -x "boo" grep.txt

Print extra lines (A/B/C)
- grep -A2 "aard" grep.txt

Search for two expressions
- egrep "<1>|<2>" grep.txt

**RAIL GREP**
great for checking lots of files quickly, used heavily in SANS FOR572
- Ex: grep -rail "bo" *
- Ex: grep -rai "bo" *

Windows equiv is Agent Ransack, handy for FOR508 KAPE outputs

**Cut**
cuts out text from input based on a delimiter
- Doesnt work too well with differing whitespace
	ex: cat /etc/passwd | cut -d: -f1
	ex: cat /etc/passwd | cut -d: -f1,3

**Translate**
translates and changes single character, useful for windows registery (shifting characters like a caesar cypher)
- -s = replaces
- -d = delete
ex: echo simon | tr "s" "S"
ex: echo Encode | tr "[n-za-nM-ZA-m]" ''

**Word count**
Count words, lines, and / or characters
- useful for gauging frequency
ex:
	wc -w grep.txt
	wc -l grep.txt
	wc -c grep.txt : 

**Sort**
Sorts the input alphabetically
	sort grep.txt
Sort and remove dupes
	sort -u grep.txt
Sort in descending order
	sort -bgr grep.txt

**Unique**
Removes duplicate lines
	- must be sorted first
	- Can also count occurances of lines
- ex : cat ~/.bash_history | sort | uniq
	- -c shows occurances of lines

**Stream editor**
Edits streams with regular expressions
- / can be replaced with | to deconflict special characters
Replace 'abc' with 'def' and print
- sed -e 's/abc/def/g' filename
Replace abc with def and overwrite
- Sed -i -e ''-e 's/abc/def/g' filename
Remove all # comments from file


**AWK**
simple language for text editing (not simple lol)
- supports regex and mathematics
- useful for extracting certain fields from files
- useful for breaking down logs

ex: cat access.log | grep "GET" | awk '{print &$7}'
ex : cat /var/log/syslog | awk  {'print $4 " " $7'}
	Finds column 4 and 7, and adds a space between them

**Find and locate**
Find
	Finds files or directories
		can execute commands on results
	ex : find /etc -name " * .conf"
Locate
	Faster than find by using an index
	Cron job updates it daily or run sudo updatedb
	ex: locate .conf

**Archive**
tar stands for tape archive, with the extension tar.gz or .gj
	Swap z for j, or remove z if you just want tar
ex: tar zcvf file.tar.gz path/to/file
	Create a tar.gz archive
Ex: tar zxvf file.tar.gz
	Extract a tar.gz archive

**Unzip**
Decompresses archives
	Bz2 and gz require the extension to decompress
	must not be in a read onlylocation

**Zcat**
like cat but can read files that have been gzipped (zip)
	useful as logs 
	ex: zcat /var/log/secure*.gz

**Bzcat** 
for bz zip files