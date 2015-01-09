ez
=========
jerryzhujian9 at gmail [\/dot/\] com
Tested under python 2.7
To see your python version
in terminal: python -V
or in python: import sys; print (sys.version)

To read the latest help info:
import ez; ez.help('ez')

=========
Easy stuff, including interaction with linux, mac, windows shells.  Very simple to use, similar to shell commands themselves!

This module is for easy interaction with linux, Mac OS X, Windows shell.
Usage:
1) import

2) type commands
Almost all commands support the usage of '~', '..', '.', '?', '*' in path (ls,fls only support regular expression).
Symbolic link itself is the target of file operations; the actual file should be safe.

error(msg)

fullpath(path)
pwd() or cwd()  # Returns current working director.
csd(), csf()   # Returns current script directory, i.e. the directory where the running script is.
parentdir(path) # Returns the parent directory of a path.
joinpath(path1[, path2[, ...]])   # Returns the joined path. Supports vectorization.
splitpath(path) # Returns a list of path elements: [path, file, ext]. Supports vectorization.
cd(path)    # Changes to a new working directory.

ls([path[, regex]], full=True)    # Returns a list of all (including hidden) files with their full paths in path, filtered by regular expression.
lsd([path[, regex]], full=True)
fls([path[, regex]])   # Returns a list of files with their full paths in flattened path (i.e. walk each subdirectory).
# the filter only works for short file name not for full file name, i.e. the file name itself not its full path
# regular expression is case-sensitive
# usage: ls(); ls(cwd()); ls(cwd(), "\.py$")

mkdir("path/to/a/directory")    # Makes a directory (also any one of the "path", "to", "a" directories if not exits).
rn(old, new) # Renames old to new.
exists(path)    # Returns the existence of path (0 or 1).
rm(path)    # Deletes a file or folder. Supports wildcards, vectorization.
cp(source, destination)  # Copies source file(s) or folder to destination. Supports wildcards, vectorization.
mv(source, destination)  # Moves source file(s) or folder to destination. Supports wildcards, vectorization.

execute(cmd)    # Executes a bash command.

pprint() # Pretty prints.
beep()  # Beeps to notify user.
which(name) # Prints where a module is and in which module a function is. which('python') returns which python is being used.
help(name)/doc(name) # name is a string, Prints the doc string of a module/class/function
    when write a module, add:
    __doc__ = three double quotes blabla three double quotes         <-----this is module's docstring, use explicit

    when write a function/class:
    def function(arg):
        three double quotes Returns, blabla three double quotes      <-----this is function's doctoring, use implicit
        return sth
ver(package_name) version(package_name), see a package's version.  package_name could be 'python'
whos(name),whos() list imported functions/packages

log(file="log.txt", mode='a', status=True) # Prints output to both terminal and a file (log.txt) globally. mode: a=append; w=overwrite

tree([path[, Folder]) # Prints a directory tree structure. Folder=True prints files in addition to folders.

[starts, ends] = regexp(string, pattern); regexp(string, pattern, method='split/match'), regexpi
regexprep(string, pattern, replace, count=0), regexprepi

sprintf(formatString, *args)
sort()
iff(expression, result1, result2)
clear(module, recursive=False)

num(string)
isempty(s)
Randomize(x) # Sets a randomization seed.
RandomizeArray(list=[])    # Shuffles a list in place.
Random(a,b) # Returns a random integer N such that a <= N <= b.
RandomChoice(seq) # Returns a random element from sequence

unique(seq), union(seq1,seq2), intersect(seq1,seq2), setdiff(seq1,seq2) in original order
    note: setdiff(seq1,seq2) may not be equal to setdiff(seq2,seq1)
            >>> unique('abracadaba')
            ['a', 'b', 'r', 'c', 'd']
            >>> unique('simsalabim')
            ['s', 'i', 'm', 'a', 'l', 'b']
            >>>
            >>> setdiff('abracadaba','simsalabim')
            ['r', 'c', 'd']
            >>> setdiff('simsalabim','abracadaba')
            ['s', 'i', 'm', 'l']
duplicate(seq) # returns a list of duplicated elements in original order

JDict() # Jerry's dictionary, customized ordered dictionary class with convient attributes and methods, see help(JDict)
Moment(timezone)    # Generates the current datetime in specified timezone, or local naive datetime if omitted.

SetClip(content)   # Copy/Write something to current clipboard
content = GetClip()   # Read out content from current clipboard and assign to a variable

lines(path='.', pattern='\.py$|.ini$|\.c$|\.h$|\.m$', recursive=True) # Counts lines of codes, counting empty lines as well.




To avoid typing email password each time, place a file named pygmailconfig.py with
EMAIL = 'someone@gmail.com'
PASSWORD = 'abcdefghik'
in the site-packages/ez folder
The functions will no longer need email/password and become like this
Mail(to, subject, body, attach=None), AddEvent(event), Sheet(fileName)

Mail([EMAIL, PASSWORD, ] to, subject, body, attach=None)
AddEvent([EMAIL, PASSWORD, ] event)     on DATE at TIME for DURATION in PLACE

Sheet([EMAIL, PASSWORD, ] fileName)
    returns a sheet object representing "Sheet 1"

    your google account doesn't have to the owner of this sheet, as long as you can edit it.
    but you need to initialize/create this sheet and maybe the header by hand to begin with
    the header could have spaces, ? etc, and when they are used as the keywords of dictionary, they are all converted to lowercase and all illegal characters are removed e.g. Delayed Test_date?  --> delayedtestdate

    fileName should be unique, can have spaces


GetRows(query=None, order_by=None,
        reverse=None, filter_func=None)
    :param query:
        A string structured query on the full text in the worksheet.
          [columnName][binaryOperator][value]
          Supported binaryOperators are:
          - (), for overriding order of operations
          - = or ==, for strict equality
          - <> or !=, for strict inequality
          - and or &&, for boolean and
          - or or ||, for boolean or.
    :param order_by:
        A string which specifies what column to use in ordering the
        entries in the feed. By position (the default): 'position' returns
        rows in the order in which they appear in the GUI. Row 1, then
        row 2, then row 3, and so on. By column:
        'column:columnName' sorts rows in ascending order based on the
        values in the column with the given columnName, where
        columnName is the value in the header row for that column.
    :param reverse:
        A string which specifies whether to sort in descending or ascending
        order.Reverses default sort order: 'true' results in a descending
        sort; 'false' (the default) results in an ascending sort.
    :param filter_func:
        A lambda function which applied to each row, Gets a row dict as
        argument and returns True or False. Used for filtering rows in
        memory (as opposed to query which filters on the service side).
    :return:
        A list of row dictionaries.


UpdateRow(row_data):
    Update Row (By ID).

    Only the fields supplied will be updated.
    :param row_data:
        A dictionary containing row data. The row will be updated according
        to the value in the ID_FIELD.
    :return:
        The updated row.


UpdateRowByIndex(index, row_data):
    Update Row By Index

    :param index:
        An integer designating the index of a row to update (zero based).
        Index is relative to the returned result set, not to the original
        spreadseet.
    :param row_data:
        A dictionary containing row data.
    :return:
        The updated row.


InsertRow(row_data):
    Append Row at the end

    :param row_data:
        A dictionary containing row data.
    :return:
        A row dictionary for the inserted row.


DeleteRow(row):
    Delete Row (By ID).

    Requires that the given row dictionary contains an ID_FIELD.
    :param row:
        A row dictionary to delete.


DeleteRowByIndex(index):
    Delete Row By Index

    :param index:
        A row index. Index is relative to the returned result set, not to
        the original spreadsheet.


DeleteAllRows():
    Delete All Rows