# Poor Man's Issue Tracker

This is a poor man's issue tracker. It's a loosely defined set of conventions
for using the filesystem as an issue tracker. Tools ([such as these](https://github.com/driusan/IssueTrackerTools)) can be written to write
or read or write directories following this convention. Track the whole thing
with git, and you can call it a distributed issue tracker.

The conventions defined here can be parsed into a database (which should be 
gitignored if using something like sqlite) for efficiency of querying in an
http frontend to an issues directory.

## Issue Conventions

There should be a top level directory named issues.

Any subdirectory of the issues/ directory is considered an issue. The 
directory name should be a short human readable description of the issue 
and can be considered the issue title. Dashes should be interpreted as 
spaces and n > 1 dashes should be interpreted as n-1 dashes when 
converting directory name to a human readable issue title.

You can put any files you want in an issue subdirectory, but there are 
some basic conventions that should be followed for the following files 
(and you should consider using git annex instead of git for tracking any
large files):

`Description`: This file contains free form text describing the issue. 
               It can be interpreted as markdown format.

`Status`: The first line of this file, after trimming beginning/end of 
          line whitespace defines the status of the issue. It can be 
          arbitrary text and the status value is case-insensitive.

          If there is a colon in the text, the part before the first 
          colon is considered the status, and the part after the value 
          of the status.

          Some examples statuses might be `Open`, `Assigned:driusan`, or `Wtf`

          Only the first line defines the status, but tools should preserve
          the rest of the file when modifying it. A user might manually 
          include, for instance, information on why this status is defined 
          for this issue.

`Priority`: The first line of this file, after trimming beginning/end of 
            line whitespace, should be interpreted as a number which
            defines the Priority of this issue. Higher numbers have higher 
            priority. Negative numbers (or real numbers) are perfectly valid. 
            Interpretation of complex numbers is left as an exercise to the 
            reader.

            Only the first line defines the priority, but tools should
            preserve the rest of the file when modifying it. A user might 
            manually include, for instance, information on why this priority 
            is assigned to this issue.

`blockedby`: This subdirectory of an issue contains files where the file 
             name is the name of some other bug blocking this issue. It can 
             optionally be a symlink, but it's equally valid to just be an 
             empty file (or a file containing text, such as a reason why 
             the other issue blocks.)
             
             Commandline tools (or http implementations) should ensure these 
             names are updated in other issues pointing to this if an issue is 
             renamed.

`tags`: This subdirectory contains empty files with tags that can be used 
        to categorize this issue.
