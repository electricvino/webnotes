---
tags:
  - python
lang: python
---
Isolated space where you can work on your Python projects seperately form system-installed Python.  Setup libraries and dependencies without affecting the system.

https://docs.python.org/3/library/venv.html

	python -m venv /path/to/new/virtual/environment

## How venvs work[](https://docs.python.org/3/library/venv.html#how-venvs-work "Link to this heading")

When a Python interpreter is running from a virtual environment, [`sys.prefix`](https://docs.python.org/3/library/sys.html#sys.prefix "sys.prefix") and [`sys.exec_prefix`](https://docs.python.org/3/library/sys.html#sys.exec_prefix "sys.exec_prefix") point to the directories of the virtual environment, whereas [`sys.base_prefix`](https://docs.python.org/3/library/sys.html#sys.base_prefix "sys.base_prefix") and [`sys.base_exec_prefix`](https://docs.python.org/3/library/sys.html#sys.base_exec_prefix "sys.base_exec_prefix") point to those of the base Python used to create the environment. It is sufficient to check `sys.prefix != sys.base_prefix` to determine if the current interpreter is running from a virtual environment.

A virtual environment may be “activated” using a script in its binary directory (`bin` on POSIX; `Scripts` on Windows). This will prepend that directory to your `PATH`, so that running **python** will invoke the environment’s Python interpreter and you can run installed scripts without having to use their full path. The invocation of the activation script is platform-specific (`_<venv>_` must be replaced by the path to the directory containing the virtual environment):

|Platform|Shell|Command to activate virtual environment|
|---|---|---|
|POSIX|bash/zsh|`$ source _<venv>_/bin/activate`|
|fish|`$ source _<venv>_/bin/activate.fish`|
|csh/tcsh|`$ source _<venv>_/bin/activate.csh`|
|pwsh|`$ _<venv>_/bin/Activate.ps1`|
|Windows|cmd.exe|`C:\> _<venv>_\Scripts\activate.bat`|
|PowerShell|`PS C:\> _<venv>_\Scripts\Activate.ps1`|