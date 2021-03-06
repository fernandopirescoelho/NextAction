NextAction
==========

A more GTD-like workflow for Todoist. Uses the REST API to add and remove a `@next_action` label from tasks.

This program looks at every list in your Todoist account.
Any list that ends with `--` or `=` is treated specially, and processed by NextAction.

Note that NextAction requires Todoist Premium to function properly, as labels are a premium feature.

Requirements
============

* Python 2.6, Python 3.0+ is unsupported at the moment
* ```python-dateutil``` package.

Activating NextAction
=====================

Sequential list processing
--------------------------
If a list ends with `--`, the top level of tasks will be treated as a priority queue and the most important will be labeled `@next_action`.
Importance is determined by:
 1. Priority
 2. Due date
 3. Order in the list

`@next_action` waterfalls into indented regions. If the top level task that is selected to receive the `@next_action` label has subtasks, the same algorithm is used. The `@next_action` label is only applied to one task.

Parallel list processing
------------------------
If a list name ends with `=`, the top level of tasks will be treated as parallel `@next_action`s.
The waterfall processing will be applied the same way as sequential lists - every parent task will be treated as sequential. This can be overridden by appending `=` to the name of the parent task.

Executing NextAction
====================

You can run NexAction from any system that supports Python, and also deploy to Heroku as a constant running service

Running NextAction
------------------

NextAction will read your environment to retrieve your Todoist API key, so to run on a Linux/Mac OSX you can use the following commandline

    TODOIST_API_KEY="XYZ" python nextaction.py

Heroku Support
--------------

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

This package is ready to be pushed to a Heroku instance with minimal configuration values:

* ```TODOIST_API_KEY``` - Your Todoist API Key
* ```TODOIST_NEXT_ACTION_LABEL``` - The label to use in Todoist for next actions (defaults to next_action)