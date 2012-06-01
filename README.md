sql-script-tester
=================

This tool makes it easier to run many SQL scripts in order, with dependencies in a repeatable fashion.  It was originally designed to help test a large database model that contains many modules.  The modules are optional, but they do have dependencies.  This tool allows you to automate the testing of all of these dependencies.

The tool will first review the XML file given to it on the command line, and build a dependency tree.  Using the tree it will then run the required SQL scripts in order.  It will also use a predefined delete script to clear out the database, and test the next set of dependencies.  This way, all possible combinations (as they are mapped in the XML file) will be tested.  Each test will report any SQL errors that were found during the execution.

You can also define multiple database connections and "start" points, this allows you to test against multiple RDBMSs, as long as there is a class for them in the tool.  Currently the tool supports Oracle and SQL Server.

To run the tool:
python sql-script-tester.py /path/to/XML/file.xml

The tool will write the the console, and to a log file.  The log file is specified in the XML file, per connection.