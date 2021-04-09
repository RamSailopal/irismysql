 AUTHOR - Raman Sailopal

 BACKGROUND - Utility to translate mysql tables into IRIS globals

 PREREQUISITES - It is assumed that a working version of Intersystems IRIS as well as mysql or mariadb is running

                 It is also assumed that the iriscmd is installed as instructed here - https://github.com/RamSailopal/iriscmd

 PARAMETERS - 
            - 1 - User name for mysql
            - 2 - Password for mysql
            - 3 - mysql host to connect to
            - 4 - mysql user name
            - 5 - mysql password
            - 6 - Intersystems IRIS instance name
            - 7 - Intersystems IRIS namespace

 USAGE - irismysql "sqluser" "sqlpass" "localhost" "test" "test_tab" "IRIS" "USER"

 EXAMPLE - 

 Assuming a mysql table test_tab in database test described as follows:

    +-------+-------------+------+-----+---------+-------+
    | Field | Type        | Null | Key | Default | Extra |
    +-------+-------------+------+-----+---------+-------+
    | col1  | double      | NO   |     | NULL    |       |
    | col2  | double      | NO   |     | NULL    |       |
    | col3  | varchar(50) | NO   | PRI | NULL    |       |
    +-------+-------------+------+-----+---------+-------+
    3 rows in set (0.00 sec)

 And with data:

    +--------+--------+-----------+
    | col1   | col2   | col3      |
    +--------+--------+-----------+
    | 1.5142 | 0.7207 | TEST1     |
    | 3.5012 |  0.479 | TEST2     |
    | 0.0134 | 0.0027 | TEST3     |
    | 3.8937 | 1.0071 | TEST4     |
    +--------+--------+-----------+
4 rows in set (0.00 sec)

 Running the utility will create a global as follows:

    Global ^test.testtab
    ^test.testtab("TEST1","col1")=1.5142
                          "col2")="0.7207"
    ^test.testtab("TEST2","col1")=3.5012
                          "col2")="0.479"
    ^test.testtab("TEST3","col1")="0.0134"
                          "col2")="0.0027"
    ^test.testtab("TEST4","col1")=3.8937
                          "col2")=1.0071

 IMPORTANT - The utility will abort if there is no primary key assigned to any columns in the table as the primary key will be translated to the primary key for the global
       
