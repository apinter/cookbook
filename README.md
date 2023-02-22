Cookbook Documentation
====================

## Reviewing process
```
new document ------> review on structure and contents #1 ------> review on language, style and punctuation #1
                                                                                        |
                                                                                        |
marked "ready" <--- review on language #2 <--- review on contents #2  <------
```

## Getting started
### Understand the repo structure
```
... 
Pipfile           <<< project dependencies in pipenv format. That is what 'pipenv install' operates on.
requirements.txt  <<< project dependencies in pip format. Added for compatibility.
pyproject.toml    <<< project dependencies in poetry format. That is what 'poetry install' operates on.
project/    <<< 'cd' in here to run mkdocs commands (pipenv commands are to be run from the root directory)
    docs/   <<< WHERE YOU WRITE DOCS. You will be adding or editing files there.
    mkdocs.yml <<< build config, but also used as Table of Contents. If you add a new file, reference it there.
    ...
...
```
`.gitignore` should not let you commit any `build` directory. Please make sure that is the case.

### Setup your work environment
You can either install mkdocs from pip or from a virtual environment.

It's highly recommended to use a virtual environment manager and not `pip`, so that the dependencies of this project won't mess with your system-wide python packages / modules. Especially important if you're using Python for other needs like development or scripting. You still need to run pip once to install your favorite virtual environment manager.

## Pipenv installation

We're using pipenv, which you install on most Linux distributions with: `pip3 install --user pipenv`. Then you'll need to add `~/.local/bin` to your `PATH`. The best method for that depends on your shell:
* for `bash` add `PATH=$PATH:/home/your-user-name/.local/bin` to `~/.bashrc`; reload to apply changes with `source ~/.bashrc`
* for `fish` run the following command once from a fish shell: `set -Ua fish_user_paths /home/your-user-name/.local/bin`; start a fresh shell with `exec fish`
* for `zsh` add `export PATH=$PATH/home/your-user-name/.local/bin` to `~/.zshrc`; reload to apply changes with `source ~/.zshrc`


### Clone, edit, test
1. clone this repo where you want in your home folder
2. `cd` to it and run `pipenv install` or `poetry install` to install the dependencies, and then `pipenv shell` or `poetry shell` to run the environment. 
3. finally `cd` to `project` and run you `mkdocs` commands from there.

The only important command is `mkdocs serve`; it generates the website from the source files and service it on http://127.0.0.1:8000/. 

Use it now to make sure you can build and display the website. 

Now you are read to work on the docs. You can either shut down the server with `CTRL + c` or let it run. It will auto-reload and refresh your browser whenever you save your changes.

### Get ready to open a Merge Request
If you are new to `git` read the [Gitlab MR docs](https://docs.gitlab.com/ee/user/project/merge_requests/creating_merge_requests.html). 

If you're new to Markdown read the [Mkdocs Markdown guide](https://www.markdownguide.org/tools/mkdocs/)

When you are done working, go through the checklist before opening a Merge Request against the repository or the master branch.

__Checklist__:
- [x] When doing `git checkout -b <meaningful name> <...>`, did you make sure that `meaningful name` satisfied the schema described under __Branches__ below? If not, you can still rename it using `git branch -m <new name that satisfies the schema> `.
- [x] Have you followed the style guidelines below under __Style__?
- [x] If you have added a new article:
  - a) did it land in `/project/docs`? If not, move it there.
  - b) have you added it to `mkdocs.yml` under the correct section?
- [x] Have you tested your work? If not consider the __Clone, edit, test__ section above.

## Formal constraints
### Branches
* The default branch -- the working branch -- is `main`. We will merge from one milestone to the other.
* 4 types of branch names, named after the type of commits you want to contribute to. MRs should whenever possible concern just one type of commit.

### Style
_Structure_. Each document should start with an intro stating the end goal, the important presuppositions (typically about pre-requirements) that the document is making, and an outline of the main steps on the path to the goal.

_Technical jargon_. Important and unavoidable jargon should be defined (typically inlined, with info boxes). Overall the document should be understandable by a new members of the DevOps team (think high-school textbook).

_Format_:
* reference points and path items in italics, ex: "_Settings_ > _Energy Saving_"
* action in bold, ex. "click __Yes__"
* code instructions part of a step-wise recipe between line breaks in code, ex. 
```
$ sudo zypper dup
```
* short snippets of code or not part of a step-wise recipe can be inlined as in "... run `sudo zypper dup` before anything else".
* first occurrence(s) of technical terms: italics