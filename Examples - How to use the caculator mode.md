## testFilesCreate interactive Calculator Mode 

Run as **testFilesCreate -C** 

User input required for tree depth, width, number of files per directory and size of each file
~~~
  File size requires units of B, K, M or G, the number must >1 decimals not permitted
  i.e. 750K 34M  2G and 10B (10 bytes)

  NOTES:
   Two bytes (2B) file size is the minimum to build a tree
   One byte is permitted here for information only
   SINGLE DIRECTORY only, set Depth = 1

 Data tree directry depth  (-d): 10
 Data tree directory width (-w): 5
 Files per directory       (-n): 120
 Size per file       (-f or -l): 20M

 Total number of directories :    2441405
 Total number of files       :      >100M
 Total file storage usage    :       5.46P

 SHOW DETAILS - Tree tables [y/n] y
~~~
**Tree tables** 
* Displays the calculated contents of the current calculation query plus all trees of smaller dimensions    
* Provides a directory count, files in each tree and storage that will be used.

~~~
Top Level directory (tree depth = 1) total file usage 2.34G
    This directory contains 120 files, each 20.00M
    Content counts and storage used by this top level is constant
    and unaffected by subdirectory count (tree width)


             Directory count for each tree
Tree Depth         2         3         4         5         6         7         8         9        10
          ------------------------------------------------------------------------------------------
Width   1 |         1         2         3         4         5         6         7         8         9
Width   2 |         2         6        14        30        62       126       254       510      1022
Width   3 |         3        12        39       120       363      1092      3279      9840     29523
Width   4 |         4        20        84       340      1364      5460     21844     87380    349524
Width   5 |         5        30       155       780      3905     19530     97655    488280   2441405

             File count for each tree
Tree Depth         2         3         4         5         6         7         8         9        10
          ------------------------------------------------------------------------------------------
Width   1 |       240       360       480       600       720       840       960      1080      1200
Width   2 |       360       840      1800      3720      7560     15240     30600     61320    122760
Width   3 |       480      1560      4800     14520     43680    131160    393600   1180920   3542880
Width   4 |       600      2520     10200     40920    163800    655320   2621400  10485720  41943000
Width   5 |       720      3720     18720     93720    468720   2343720  11718720  58593720     >100M

             File storage usage for each tree
Tree Depth         2         3         4         5         6         7         8         9        10
          ------------------------------------------------------------------------------------------
Width   1 |     4.69G     7.03G     9.38G    11.72G    14.06G    16.41G    18.75G    21.09G    23.44G
Width   2 |     7.03G    16.41G    35.16G    72.66G   147.66G   297.66G   597.66G     1.17T     2.34T
Width   3 |     9.38G    30.47G    93.75G   283.59G   853.12G     2.50T     7.51T    22.52T    67.58T
Width   4 |    11.72G    49.22G   199.22G   799.22G     3.12T    12.50T    50.00T   200.00T   800.00T
Width   5 |    14.06G    72.66G   365.62G     1.79T     8.94T    44.70T   223.52T     1.09P     5.46P

 Run again [y/n]
~~~
Previous example tree depth was 5 and width 10, this example tree depth is 10 and width 5. This highlights the impact of tree depth
~~~
  File size requires units of B, K, M or G, the number must >1 decimals not permitted
  i.e. 750K 34M  2G and 10B (10 bytes)

  NOTES:
   Two bytes (2B) file size is the minimum to build a tree
   One byte is permitted here for information only
   SINGLE DIRECTORY only, set Depth = 1

 Data tree directry depth  (-d): 5
 Data tree directory width (-w): 10
 Files per directory       (-n): 120
 Size per file       (-f or -l): 20M

 Total number of directories :      11110
 Total number of files       :    1333320
 Total file storage usage    :      25.43T

 SHOW DETAILS - Tree tables [y/n] y
_____________________________________________________
Tables of current selection and smaller trees.
Tree tables will wrap with small window
At full sreen tree depth >17 output will probably wrap and be messy

Top Level directory (tree depth = 1) total file usage 2.34G
    This directory contains 120 files, each 20.00M
    Content counts and storage used by this top level is constant
    and unaffected by subdirectory count (tree width)


             Directory count for each tree
Tree Depth         2         3         4         5
          ----------------------------------------
Width   1 |         1         2         3         4
Width   2 |         2         6        14        30
Width   3 |         3        12        39       120
Width   4 |         4        20        84       340
Width   5 |         5        30       155       780
Width   6 |         6        42       258      1554
Width   7 |         7        56       399      2800
Width   8 |         8        72       584      4680
Width   9 |         9        90       819      7380
Width  10 |        10       110      1110     11110

             File count for each tree
Tree Depth         2         3         4         5
          ----------------------------------------
Width   1 |       240       360       480       600
Width   2 |       360       840      1800      3720
Width   3 |       480      1560      4800     14520
Width   4 |       600      2520     10200     40920
Width   5 |       720      3720     18720     93720
Width   6 |       840      5160     31080    186600
Width   7 |       960      6840     48000    336120
Width   8 |      1080      8760     70200    561720
Width   9 |      1200     10920     98400    885720
Width  10 |      1320     13320    133320   1333320

             File storage usage for each tree
Tree Depth         2         3         4         5
          ----------------------------------------
Width   1 |     4.69G     7.03G     9.38G    11.72G
Width   2 |     7.03G    16.41G    35.16G    72.66G
Width   3 |     9.38G    30.47G    93.75G   283.59G
Width   4 |    11.72G    49.22G   199.22G   799.22G
Width   5 |    14.06G    72.66G   365.62G     1.79T
Width   6 |    16.41G   100.78G   607.03G     3.56T
Width   7 |    18.75G   133.59G   937.50G     6.41T
Width   8 |    21.09G   171.09G     1.34T    10.71T
Width   9 |    23.44G   213.28G     1.88T    16.89T
Width  10 |    25.78G   260.16G     2.54T    25.43T

 Run again [y/n]
 ~~~


