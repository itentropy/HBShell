# HBShell

A simple but powerful replacement for ./hbase shell

## Installation

Execute:

    $ wget --no-check-certificate https://codeload.github.com/xxjapp/HBShell/zip/master
    $ unzip master
    $ mv HBShell-master HBShell
    $ cd HBShell/
    $ chmod +x run.rb
    $ ./run.rb

## System Shell Commands

    $ ruby run.rb

## HBShell Commands

### CLEAR - clear table contents

    ** WARNING : 'clear'(and its alias) will clear contents of all tables in database
    ** NOTE    : use 'clear! ...' to force clear

      usage   : clear [table_pattern]
      example : clear ^test_table
      alias   : [cle, clr]

### CONNECT - show current quorums or set new quorums temporarily

    ** NOTE: for permanent change of quorums, modify hosts file
    [windows: C:\Windows\System32\drivers\etc\hosts / linux: /etc/hosts]
    or change value of 'hbase.zookeeper.quorum' in conf/hbase-site.xml

      usage   : connect [quorums_separated_by_comma]
      example : connect 172.17.1.206
      alias   : [con]

### COUNT - count number of tables, rows, families, qualifiers, or values at a specified level

      usage   : count [table_pattern [row_pattern [family_pattern [qualifier_pattern [value_pattern]]]]]
      example : count ^135530186920f18b9049b0a0743e86ac3185887c5d .
      alias   : [cnt]

### CREATE - create table

      usage   : create table_name family_name1 [family_name2 ...]
      example : create test_table family1 family2
      alias   : [c, cre]

### DELETE - delete data in database

    ** WARNING : 'delete'(and its alias) will delete all tables in database
    ** NOTE    : use 'delete! ...' to force delete

      usage   : delete [table_name [row_key [family_name [qualifier_name]]]]
      example : delete test_table family1
      alias   : [d, del]

### DESCRIBE - describe the named table

      usage   : describe [table_pattern [family_pattern]]
      example : describe ^135530186920f18b9049b0a0743e86ac3185887c5d
      alias   : [des]

### FILTER - scan database data with given filter, other_pattern will be applied like grep finally

      usage   : filter [table_pattern [row_pattern [family_pattern [qualifier_pattern [value_pattern]]]]] other_pattern
      example : filter ^135530186920f18b9049b0a0743e86ac3185887c5d fullpath
      alias   : [f]

### GET - get contents of database, table, row, family or qualifier

      usage   : get [table_name [row_key [family_name [qualifier_name]]]]
      example : get 135530186920f18b9049b0a0743e86ac3185887c5d f30dab5e-4b42-11e2-b324-998f21848d86file
      alias   : [g]

### HELP - show help message

      usage   : help [topic1 [topic2 ...]]
      example : help filter get
      alias   : [h]

### HISTORY - show command history

      usage   : history [count [pattern]]
      example : history 3 get
      alias   : [his]

### LIST - list database data at a specified level

      usage   : list [table_pattern [row_pattern [family_pattern [qualifier_pattern [value_pattern]]]]]
      example : list ^135530186920f18b9049b0a0743e86ac3185887c5d file
      alias   : [l, ls]

### MULTILINE - show current multiline status or set new multiline status temporarily

    ** NOTE: for permanent change of multiline status, modify setting file [conf/config.ini]

      usage   : multiline [0, false or 1, true]
      example : multiline false
      alias   : [m]

### PUT - put a cell 'value' at specified table/row/family:qualifier

      usage   : put table_name row_key family_name qualifier_name value
      example : put test_table row1 family1 qualifier1 value1
      alias   : [p]

### QUIT - quit this shell

      usage   : quit
      example : quit
      alias   : [e, q, exit]

### READONLY - show current readonly status or set new readonly status temporarily

    ** NOTE: for permanent change of readonly status, modify setting file
    [conf/config.ini]

      usage   : readonly [0, false or 1, true]
      example : readonly false
      alias   : [ro]

### REG_DELETE - delete data in database with given filter

    ** WARNING : 'delete'(and its alias) will delete all tables in database
    ** NOTE    : use 'delete! ...' to force delete

      usage   : reg_delete [table_pattern [row_pattern [family_pattern [qualifier_pattern [value_pattern]]]]]
      example : reg_delete ^test_table family1
      alias   : [rd]

### RENAME - rename table in hbase

      usage   : rename old_table_name new_table_name
      example : rename test_table test_table2
      alias   : [rn, ren]

### RUN - run external hbshell command file

      usage   : run file_path
      example : run ./commands.hbc
      alias   : [r]

### SCAN - scan database data with given filter

      usage   : scan [table_pattern [row_pattern [family_pattern [qualifier_pattern [value_pattern]]]]]
      example : scan ^135530186920f18b9049b0a0743e86ac3185887c5d . fileinfo
      alias   : [s]

### VERSION - show version message

      usage   : version
      example : version
      alias   : [v, ver]

## Note 1) - Keyboard in linux

     - all control keys are not usable before jline added
     - thanks to jline, arrow left/right/up/down are usable, but
     - backspace and delete are switched (resolved by MyUnixTerminal)
     - home/end, page up/down are not usable (resolved by MyConsoleReader partially)
      - the following text in pasting text will act as control keys
       - '1~' -> home, go to begin of line
       - '2~' -> insert, do nothing
       - '4~' -> end, go to end of line
       - '5~' -> page up, move to first history entry
       - '6~' -> page down, move to last history entry

## NOTE 2) - Command modifier/row limit

     - all commands can be added with a row limit number to only operate on first found rows

## NOTE 3) - Command modifier/quiet mode

     - all commands can be added with a '-' mark to execute without logging to console and normal log file

## NOTE 4) - Command modifier/force to execute

     - all commands can be added with a '!' mark to execute without confirmation

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
