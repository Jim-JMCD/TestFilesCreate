## Examples of test data creation 

Example 1

* Create a directory tree that is three levels deep, each level containing five subdirectories i.e.tree depth = 5 and tree width = 3. **[ -d 5 -w 3 ]** 
* Each directory to be filed with fifty 15MiB files, all files are identical. **[ -n 50 -f 50M ]** _-r is not used_
* Each file filled with the first 28 printable characters of the ASCII character set. **[ -P 28 ]**

This interactive example displays the output to expect when you proceed with file creation. The computer time is used, not UTC.      
~~~
$./TFileCreate -P 28 -d 3 -w 5 -f 15M -n 50

  DIRECTORTY TREE each directory contains 5 directories and 50 files
  The tree is 3 levels deep
  Output: /home/ted/testit/tfc_250919-1055-12

  All files with identical contents
  Files created are all 15M
  Storage used...... 22.71G (max potential)
  File Contents..... Random selection from a 28 char set: !"#$%&'()*+,-./0123456789:;<

  Total data directories........30
  Total data files............1550

Do you want to proceed? (y/n) y

 *** Early termination requires manual deletion of data created ****
Start Fri Sep 19 10:55:33 UTC 2025
.......... 10 directories filled Fri Sep 19 10:56:01 UTC 2025
.......... 20 directories filled Fri Sep 19 10:56:09 UTC 2025
.......... 30 directories filled Fri Sep 19 10:56:18 UTC 2025
~~~
Example 2 

Same as previous except for: 
* Output to be created in /home/ted/tmp, not the current directory. **[ -o /home/ted/tmp ]**  
* To be run in batch mode. **[ -b ]**

Notes

* Directing output to a specific directory requires the directory to exist before creating the test data.
* Batch mode does not require any user input one started.
~~~
$./TFileCreate -P 28 -d 3 -w 5 -f 15M -n 50 -o /home/ted/tmp -b

  DIRECTORTY TREE each directory contains 5 directories and 50 files
  The tree is 3 levels deep
  Output: /home/ted/tmp/tfc_250919-1055-12

  All files with identical contents
  Files created are all 15M
  Storage used...... 22.71G (max potential)
  File Contents..... Random selection from a 28 char set: !"#$%&'()*+,-./0123456789:;<

  Total data directories........30
  Total data files............1550

Start Fri Sep 19 10:55:33 UTC 2025
.......... 10 directories filled Fri Sep 19 10:56:01 UTC 2025
~~~


Example 3

* Create a directory tree with a depth of 4 and a width of 6. **[ -d 4 -w 6 ]**
* Each directory to be filed with 75 files that have random sizes between 500KiB and 2MiB. **[ -s 500K -l 2M -n 75]**
* Each file filled with the complete lower case alphabet. **[ -P 26 ]**
* Each file to be filled with its own random own of alphabet letters. **[ -r ]**
* If only the first ten letters of the alphabet required use **-P 10**
* No uppercase option available  
~~~
$./TFileCreate -P 26 -d 4 -w 6 -s 500K -l 2M -n 75 -r
  
DIRECTORTY TREE each directory contains 6 directories and 75 files
  The tree is 4 levels deep
  Output: /home/ted/testit/tfc_250919-1104-51

  File contents individually generated for each file
  Files created in a size range 500K to 2M
  Storage used...... 37.94G (max potential)
  File Contents..... Random selection from a 26 char set: abcdefghijklmnopqrstuvwxyz

  Total data directories.......258
  Total data files...........19425
~~~~
Example 4

* Create a single file **[ -d 1 -w 1 -n 1 ]**
* File size to be 500 GiB **[ -f 500G ]**
* File to be filled with random digits (0 - 9 )  **[ -r -D 10 ]**
* If only the first five digits required use **-D 5** 

~~~~
$./TFileCreate -D 10 -d 1 -w 1 -f 500G -n 1 -r

  SINGLE DIRECTORY containing 1 files

  Output: /home/bob/TF-Oct/tfc_251019-1112-58

  File contents individually generated for each file
  Files created are all 500G
  Storage used...... 500.00G (max potential)
  File Contents..... Random selection from a 10 digit set: 0123456789

  Total data directories.........1
  Total data files...............1

