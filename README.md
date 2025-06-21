# TestFilesCreate

 A small Linux app that creates test files filling them with random data in a single directory or a directory tree. 
 
 * Includes a calculator for creating data in directory trees. [ Option -C ]
 * Will create a single file to directory trees of files, minimum file size = 2 bytes   
 * Files can be identical or individully filled with random content.
 * File contents can either be printable or binary (from /dev/urandom) 
 * Files sizes can be identical or randomly sized within a given range.
 * Run either interactively or unaccompanied in batch mode. 
_______________________________________________________________________
TestFilesCreate is a Linux portable executable created from the bash script [TFile_Create](https://github.com/Jim-JMCD/Test_Files_Create) (private Github repository) using shc. 

### Dependency
This requires a bash environment to run. 
An executable created from the *shc* utility always requires bash on X64

More : [Github shc](https://github.com/neurobin/shc)   
_______________________________________________________________________

## CALCULATOR mode  (interactive, tree only) 

__TestFileCreate -C__ 
 
 *User Inputs*: Tree depth, width, number files per directory and file size
 
 *Output*: Summary, tables of data trees of current and smaller trees. Tables contain data size and file numbers for each tree
_______________________________________________________________________
## TEST DATA CREATION mode  

__DEFAULTS__
 * File contents are binary. Use -P or -D for creating compressable printable data  
 * If all files same size then contents will also be identical.  Use -r option to randomise file contents.
 * A time stamped output directory is created in users current directory. Alternatively use another directory with the -o option
 * Interactive mode, requires confirmation to proceed after providing user with a summary. See examples.

 Maximum permitted values, see __Limitations__ section    

__OPTIONS : Directory Layout__ All mandatory
For the following, _n_ is a number, minimum is 1   
* -n _n_   Number of files in each directory.
* -d _n_   Depth. How many directories deep.  
* -w _n_   Width. How many directories wide.  

Maximum permitted values, see __Limitations__ section  

Create single directory: -d 1 (-w if set, will be ignored) 

Create tree of directories: 
* Depth min is -d 2
* Width min is -w 1 and manditory  

__OPTIONS : File Size and Content__ A file size is mandatory

*Fixed File Size*
 * File sizes have to be designated by B, K, M or G. Minimum is 2B (2 bytes). Example 2KiB = 2K, 3MiB = 3M 4GiB = 4G   
 * -f Fixed file size, default [usage: -f 2K]

 _NOTE: Default content for fixed file size of printable data is:_ ALL FILES ARE IDENTICAL, use     
 * -r Random content is generated individually for every file.   

_Random File Size_
* All files individually filled with random content. 
* -s Smallest file size.
* -l Largest file size. 
* If -s is omitted, the random range starts at 2B (2 bytes) if largest file size is <1G or 1M (1MiB) if largest file size is >= 1G

__OPTIONS: Optional__
* __-P _n___   Where _n_ is a nuber in the range 1 to 95. Selects the pool of printable characters from the ASCII set. 
  * _n_ = 1 files only contain the uppercase 'A' 
  * _n_ = 2 to 26 files only contain lowercase Latin alphabet characters
  * _n_ >26 files contain printable ASCII characters. Max n = 95 

* __-D _n___  Where _n_ is a number in the range 1 to 10. Selects the pool of digit charcters from the ASCII set.
  * _n_ = 1 files only contain zeros '0'
  * _n_ > 1 files contain digits. Max n = 10

* _-o_ Output to directory that already exists.
* _-r_ Random content for fixed file sizes.
* _-o_ Output to an _existing_ directory.
  * Defaults to current working directory
  * Creates a new time stamped directory for content (tfc_YYMMDD_hhmm_ss).
* _-b_ Batch/quiet run with no user checks. Default is interactive with user input. 

__LOGGING__
* None. In batch mode user has to redirect output to a file  
* Progress indicated by time stamping every ten directories filled with files.
* The 'script' command can be used in interactive mode to record all activty. 
 
__LIMITATIONS__

Data creation bails out before any data creation if: 
* The number of directories to be created exceeds 100 million
* The number of files to be created exceeds 100 million
* If the 'shuf' command is not available 
* if the -c option not avaiable for the 'head' command.
* For x64 Linux.

If the 'seq' command is not avaiable. The character pool will not be displayed in the inital summary. The seq command is not required for file creation.

Binary data is generated from /dev/urandom. This data will not compress that well. Binary data that is stored/transmitted may render data deduplication and compression ineffective.  
___Validate contents: all Files:___

    od -N <bytes> -Ax -t x1z <file name>
     
* Where \<bytes\> is the number to check from beginning of file.
* Non-printable characters will appear as "dots"

___Validate printable character distribution:___
   
    od -a <file name>  | cut -b 9- | tr " " \\n | egrep -v "^$" | sort | uniq -c
    OR
    sed 's/\(.\)/\1\n/g' <file name> | sort | uniq -c
    
    
_Output_
* Column 1 : Character count
* Column 2 : Character being counted. This column should only contain a single charcter, if not then file contents is binary data.

___Validate printable character pool count:___

    od -a <file name>  | cut -b 9- | tr " " \\n | egrep -v "^$" | sort | uniq -c | wc -l
    OR
    sed 's/\(.\)/\1\n/g' <file name> | sort | uniq -c | wc -l 
_________________________________________________________________________________________________________
EXAMPLES 

__TestFilesCreate -P 28 -d 3 -w 5 -f 15M -n 50__

    DIRECTORY TREE each directory contains 5 directories and 50 files
    The tree is 3 levels deep
    Output: /home/ted/test/tfc_240930-1759-37
    All files with identical contents
    Files created are all 15M
    Storage used...... 22.71G (max potential)
    File Contents..... Random selection from the 28 char set: !"#$%&'()*+,-./0123456789:;<
    Total data directories........30
    Total data files............1550
    Do you want to proceed? (y/n)

__TestFilesCreate -D 5 -d 1 -f 600K -n 1000 -r -o /home/ted/test__

    SINGLE DIRECTORY containing 1000 files
    Output: /home/ted/test/tfc_240930-1802-53
    Random data created individually for all files
    Files created are all 600K
    Storage used...... 585.94M (max potential)
    File Contents..... Random selection from the 5 digit set: 01234
    Total data directories.........1
    Total data files............1000
    Do you want to proceed? (y/n)
