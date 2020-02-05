# Insum PL/SQL &amp; SQL Coding Guidelines

## Introduction

In 2019, Rich Soule of Insum forked these guidelines from the Trivadis guidlines and changed most of the rules to comply with Insum coding standards and added many new guidelines. New rules were also suggested in the Trivadis Issues, and while many were adopted, some (and some we consider very important) were not.

Trivadis published their guidelines for PL/SQL &amp; SQL in 2009 in the context of the DOAG conference in Nuremberg. Since then these guidelines have been continuously extended and improved. Now they are managed as a set of markdown files. This makes the the guidelines more adaptable for individual application needs and simplifies the continous improvement.

## HTML format

Coming Soon!
HTML is the primary output format. [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) is used to generate static HTML files and [Mike](https://github.com/jimporter/mike) to publish version specific variants. The following sites are available:

Link                                                                 | Content
-------------------------------------------------------------------- | -------
Coming Soon                                                          | Latest Release
[Snapshot](https://insum-labs.github.io/plsql-and-sql-coding-guidelines/master/) | Current version based on the master branch, typically a snapshot version of the coming release

## PDF format

Coming Soon                                                         
PDF is the secondary output format. [wkhtmltopdf](https://wkhtmltopdf.org/) is used to generate the [PLSQL-and-SQL-Coding-Guidelines.pdf]

## Releases

Coming Soon

## Issues
Please file your bug reports, enhancement requests, questions and other support requests within [Github's issue tracker](https://help.github.com/articles/about-issues/).

* [Questions]()
* [Open enhancements]()
* [Open bugs]()
* [Submit new issue]()

## How to Contribute

1. Describe your idea by [submitting an issue]()
2. [Create a branch](https://help.github.com/articles/creating-and-deleting-branches-within-your-repository/), commit and publish your changes and enhancements
3. [Create a pull request](https://help.github.com/articles/creating-a-pull-request/)

## How to Build the HTML Site and PDF File

1. Install Docker in your environment
   * [Install Docker Desktop for Mac](https://docs.docker.com/docker-for-mac/install/)
   * [Install Docker Desktop on Windows](https://docs.docker.com/docker-for-windows/install/)
   * [Install Docker Server on Linux](https://docs.docker.com/install/#server)
2. [Fork this respository](https://github.com/insum-labs/plsql-and-sql-coding-guidelines/fork)
3. For Windows users only
   * Install [Git for Windows](https://gitforwindows.org/), it provides Git command line tools, a GUI and a Bash emulator
4. Check/change the version in [mkdocs.yml](mkdocs.yml)
5. Open a terminal window in the [tools](tools) folder 
   * Build/update the PDF file
     run `./genpdf.sh`.
   * Test the HTML site locally
     run `./serve.sh` and open [http://localhost:8000](http://localhost:8000)
   * Deploy HTML site
     run `./mike.sh deploy master`.
   * Set default version (HTML redirect)
     run `./mike.sh set-default master`.
6. `commit` changes and `push` all branches.
   * `git commit`
   * `git push --all origin`

## License

The Insum PL/SQL & SQL Coding Guidelines are licensed under the Apache License, Version 2.0. You may obtain a copy of the License at <http://www.apache.org/licenses/LICENSE-2.0>.
