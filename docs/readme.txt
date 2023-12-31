typespeed v0.6.5
----------------
Test your typing speed and get your fingers' CPS.

Index:
1 Latest Version
2 Overview
3 Usage
4 High Score File Format
5 Rule Sets
6 Frequently Asked Questions
7 Contact


1 Latest Version
----------------

You can download latest version of typespeed on typespeed's website
located at http://tobias.eyedacor.org/typespeed/.


2 Overview
----------

Typespeed gives your fingers' cps (total and correct), typoratio and
some points to compare with your friends.

Typespeed's idea is ripped from ztspeed (a dos game made by Zorlim).
Idea of the game should be clear to anyone, just type and type it fast
or be a loser.


3 Usage
-------

Please refer to typespeed's manual page.


4 High Score File Format
------------------------

In this section, the new high score file format will be explained.
The new way to save high scores is especially useful if you are
interested in creating statistics about your scores.

The file format has changed with v0.6.0 into a csv format (character
separated values).  The separation character in use is tab ('\t' if you
speak C).  If a tab is used in a field, it is escaped with a
backslash (\).  If a backslash is used in a field, it is escaped with
another backslash.

That being said, the field values have the following meaning:

Field | Name           | Meaning
------+----------------+-----------------------------------------------
  1   | score          | How many points has the player gathered?
  2   | total count    | How many characters has the player entered?
  3   | enter offset   | Count of enter/space pressed to finish a word
  4   | name           | What name has the player?
  5   | word list      | What word list was in use?
  6   | rule set       | Which rule set was in use?
  7   | duration       | How long lasted game session? (hundreds of seconds)
  8   | sinit          | Value used to fill in random number generator

Example:
227     229     39      Tobias  words.unix      rule.classic    5600    0

This means that player "Tobias" played word list "words.unix" with rule
set "rule.classic".  Further more it is easy to tell that no cheat mode
was in use, because an enter offset of 39 exists.  In cheat mode, this
value would be 0, because no enter/space has to be pressed.

The value for random number generator is unknown (0).  This means that
this entry has been converted with convert.  The score of player "Tobias"
was 227, with 229 characters typed in total.  The game lasted 56 seconds.

With these information, cps, tcps and typo ratio can be calculated:

cps = (score + enter offset) / duration * 100
tcps = (total count + enter offset) / duration * 100
typo ratio = (1 - (score + enter offset) / (total count + enter offset)) * 100


5 Rule Sets
-----------

If no default values have been changed, an example rule set can be found
at /usr/local/share/typespeed/rules/template.

You have to use "rule." as a prefix for your file to be treated as a rule
set.

Although all lines starting with "#" are handled as comments, the first
line is special.  In the first line, you have to specify the description
of the rule set - this line MUST start with #.

All other values should be commented perfectly fine.


6 Frequently Asked Questions
----------------------------

Q: Is typespeed's timing broken? I have used some other programs to
   determine my CPS and it is much higher than with typespeed.

A: No, typespeed's timing works fine.  But you are right, too.  At the
   beginning of a typespeed session, there are only a few words on
   screen.  Just try to contentrate on your typing rate.  If you are a
   fast typer, you will often wait and type nothing until something new
   appears.  At the end, you will be indeed faster than measured CPS.
   Typespeed calculates the whole time to measure CPS so the waiting at
   the beginning kills your high rates.  If you want to circumvent this,
   try to write an own rule set with min words != 0 and a high speed
   rate.  This way, you can measure your real CPS.

Q: There are no high scores listed in high score menu, but there are
   definitely some in my high score file.  What is going wrong?

A: I guess you have not selected the right rule set.  If you do not
   change anything, you have the default rule set.  To see other high
   scores, you have to change the rule set first (menu point 6).

   Another possibility is that you have created or removed a user-
   specific configuration file.  If that is the case, typespeed switched
   from system-wide high score to user-specific high score (or vice
   versa).  To get back to user-specific high score, just create an
   empty configuration file (~/.typespeed/config).


7 Contact
---------

Bugs/Ideas/Comments to Tobias Stoeckmann <tobias@bugol.de>.

