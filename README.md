# utl_filling_in_missing_values_using_a_second_table
Filling in missing values using a second table
    Filling in missing values using a second table

    Orginal topic: Missing values in two data set and merge it to one

    You are welcome hear and not on hold.
    If I had another 15 minutes I couyld provide the R/IML code.
    I expect it to be quite elegant in R or IML.\
    My python skills are not as strong as R and SAS.

    github
    https://goo.gl/cDGsie
    https://github.com/rogerjdeangelis/utl_filling_in_missing_values_using_a_second_table

    https://goo.gl/Q5zkex
    https://stackoverflow.com/questions/47648421/missing-values-in-two-data-set-and-merge-it-to-one


    INPUT
    =====

       WORK.A total obs=6

          TREE     HEIGHT    AGE    YIELD    PROFIT

         Apple       18       20      14       105
         Pear        12       12       .         .
         Cherry       .        .       9       105
         Apples       .        .      10        75
         Pears        9        8       8         .
         Apple1       8        9       .        45

       WORK.B total obs=6

          TREE     HEIGHT    AGE    YIELD    PROFIT

         Apple        .        .      14         .
         Pear         .       12      10       96.0
         Cherry      13       14       9      105.0
         Apples      14       15       .         .
         Pears        9        .       8       76.8
         Apple1       .        .       6         .


    PROCESS (ALL THE CODE)
    =======================

       proc sort data=a;by tree;run;quit;
       proc sort data=b;by tree;run;quit;

       * thanks to data _null_;
       data want;
        update a b;
        by tree;
       run;

    OUTPUT
    ======

       WORK.WANT total obs=6

        TREE     HEIGHT    AGE    YIELD    PROFIT

       Apple       18       20      14      105.0
       Pear        12       12      10       96.0
       Cherry      13       14       9      105.0
       Apples      14       15      10       75.0
       Pears        9        8       8       76.8
       Apple1       8        9       6       45.0

    *                _              _       _
     _ __ ___   __ _| | _____    __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|

    ;

    data A ;
    input Tree$ Height Age Yield Profit;
    cards4;
    Apple 18 20 14 105
    Pear 12 12 . .
    Cherry . . 9 105
    Apples . . 10 75
    Pears 9 8 8 .
    Apple1 8 9 . 45
    ;;;;
    run;quit;

    data B;
    input Tree$ Height Age Yield Profit;
    cards4;
    Apple . . 14 .
    Pear . 12 10 96
    Cherry 13 14 9 105
    Apples 14 15 . .
    Pears 9 . 8 76.8
    Apple1 . . 6 .
    ;;;;
    run;quit;

    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;

    proc sort data=a;by tree;run;quit;
    proc sort data=b;by tree;run;quit;

    * thanks to data _null_;
    data want;
     update a b;
     by tree;
    run;
