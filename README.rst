A simple VTE-based terminal.

Termite looks for ``termite.cfg`` in ``$XDG_CONFIG_HOME`` (or ``~/.config`` if
unset) and then falls back to ``$XDG_CONFIG_DIRS``.

Termite's exit status is 1 on a failure, including a termination of the child
process from an uncaught signal. Otherwise the exit status is that of the child
process.

DEPENDENCIES
============

A vte version >= ``0.34``. A patch is required to expose the functions needed
for keyboard selection.

KEYBINDINGS
===========

INSERT MODE
-----------

+----------------------+---------------------------------------------+
| ``ctrl-shift-x``     | activate url hints mode                     |
+----------------------+---------------------------------------------+
| ``ctrl-shift-r``     | reload configuration file                   |
+----------------------+---------------------------------------------+
| ``ctrl-shift-c``     | copy to CLIPBOARD                           |
+----------------------+---------------------------------------------+
| ``ctrl-shift-v``     | paste from CLIPBOARD                        |
+----------------------+---------------------------------------------+
| ``ctrl-shift-u``     | unicode input (standard GTK binding)        |
+----------------------+---------------------------------------------+
| ``ctrl-tab``         | start scrollback completion                 |
+----------------------+---------------------------------------------+
| ``ctrl-shift-space`` | start command mode                          |
+----------------------+---------------------------------------------+
| ``ctrl-shift-t``     | open terminal in the current directory [1]_ |
+----------------------+---------------------------------------------+
| ``ctrl-shift-up``    | scroll up a line                            |
+----------------------+---------------------------------------------+
| ``ctrl-shift-down``  | scroll down a line                          |
+----------------------+---------------------------------------------+
| ``shift-pageup``     | scroll up a page                            |
+----------------------+---------------------------------------------+
| ``shift-pagedown``   | scroll down a page                          |
+----------------------+---------------------------------------------+

.. [1] The directory can be set by a process running in the terminal. For
       example, with zsh:

       .. code:: sh

            if [[ $TERM == xterm-termite ]]; then
              . /etc/profile.d/vte.sh

              __vte_ps1

              chpwd() {
                __vte_ps1
              }
            fi

COMMAND MODE
------------

+--------------------------+-----------------------------------------------------------+
| ``escape``               | deactivate command mode                                   |
+--------------------------+-----------------------------------------------------------+
| ``x``                    | activate url hints mode                                   |
+--------------------------+-----------------------------------------------------------+
| ``v``                    | visual mode                                               |
+--------------------------+-----------------------------------------------------------+
| ``V``                    | visual line mode                                          |
+--------------------------+-----------------------------------------------------------+
| ``ctrl-v``               | visual block mode                                         |
+--------------------------+-----------------------------------------------------------+
| ``hjkl`` or arrow keys   | move cursor left/down/up/right                            |
+--------------------------+-----------------------------------------------------------+
| ``w`` or ``shift-right`` | forward word                                              |
+--------------------------+-----------------------------------------------------------+
| ``b`` or ``shift-left``  | backward word                                             |
+--------------------------+-----------------------------------------------------------+
| ``W`` or ``ctrl-right``  | forward WORD (non-whitespace)                             |
+--------------------------+-----------------------------------------------------------+
| ``B`` or ``ctrl-left``   | backward WORD (non-whitespace)                            |
+--------------------------+-----------------------------------------------------------+
| ``0``                    | move cursor to the first column in the row                |
+--------------------------+-----------------------------------------------------------+
| ``^``                    | beginning-of-line (first non-blank character)             |
+--------------------------+-----------------------------------------------------------+
| ``$``                    | end-of-line                                               |
+--------------------------+-----------------------------------------------------------+
| ``g``                    | jump to start of first row                                |
+--------------------------+-----------------------------------------------------------+
| ``G``                    | jump to start of last row                                 |
+--------------------------+-----------------------------------------------------------+
| ``ctrl-u``               | move cursor half a screen up                              |
+--------------------------+-----------------------------------------------------------+
| ``ctrl-d``               | move cursor half a screen down                            |
+--------------------------+-----------------------------------------------------------+
| ``y``                    | copy to CLIPBOARD                                         |
+--------------------------+-----------------------------------------------------------+
| ``/``                    | forward search                                            |
+--------------------------+-----------------------------------------------------------+
| ``?``                    | reverse search                                            |
+--------------------------+-----------------------------------------------------------+
| ``u``                    | forward url search                                        |
+--------------------------+-----------------------------------------------------------+
| ``U``                    | reverse url search                                        |
+--------------------------+-----------------------------------------------------------+
| ``o``                    | open the current selection as a url                       |
+--------------------------+-----------------------------------------------------------+
| ``Return``               | open the current selection as a url and exit command mode |
+--------------------------+-----------------------------------------------------------+
| ``n``                    | next search match                                         |
+--------------------------+-----------------------------------------------------------+
| ``N``                    | previous search match                                     |
+--------------------------+-----------------------------------------------------------+
| ``+``                    | increase font size                                        |
+--------------------------+-----------------------------------------------------------+
| ``-``                    | decrease font size                                        |
+--------------------------+-----------------------------------------------------------+

URL SELECT MODE
---------------

+----------------------+-------------------------------------------------------+
| ``ctrl-shift-z``     | enter url select mode                                 |  
+----------------------+-------------------------------------------------------+
| ``ctrl-shift-y``     | copy currently select url to CLIPBOARD                |
+----------------------+-------------------------------------------------------+
| ``ctrl-shift-o``     | open the currently select url                         |
+----------------------+-------------------------------------------------------+
| ``Return``           | open the currently selected url and exit command mode |
+----------------------+-------------------------------------------------------+
| ``j``                | forward url search                                    |
+----------------------+-------------------------------------------------------+
| ``k``                | reverse url search                                    |
+----------------------+-------------------------------------------------------+

During scrollback search, the current selection is changed to the search match
and copied to the PRIMARY clipboard buffer.

With the text input widget focused, up/down (or tab/shift-tab) cycle through
completions, escape closes the widget and enter accepts the input.

After hints mode is activated, as single number or a comma separated list of
hint numbers can be entered, which will be opened in the browser.
