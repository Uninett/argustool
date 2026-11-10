:tw=72

============
Contributing
============

Dependencies
============

This tool aims for as few dependencies as possible beyond pyargus. If
you solve a problem by adding another dependency, that's reason enough
to not add your fix to the codebase. This is why we use argparse.

Commit messages
===============

1. If the change is tentative/not done, the commit message should start
   with a *lowercase* letter. That tells us it is okay to
   fixup/squash/otherwise alter the change/message. The rest of the
   points in this list don't need to be followed for these.
2. If you're happy with the change, it should start with an *uppercase*
   letter.
3. Strive for a length for the first line of at most 50 characters. This
   can be hard, we know, but it helps to keep cruft out of the first
   line: No prefixes, no emojis, no filenames, no issue numbers, PR
   numbers or urls etc. Prose, please.
4. The first line should continue the sentence "If merged, this patch
   will ...". This will force an *infinitive* of the verb, and will
   prevent commits starting with "Do". Pick a verb to start with
   instead, use a dictionary to find a suitable one if necessary.
5. More information is frequently useful, add it after a full blank line. The
   body of the message should be max. 80 characters wide, preferrably closer to
   72. This is where you can put emojis, poems, filenames, humblebrags, issue
   or PR numbers, or urls. It is not necessary to break long urls.
6. A body, if any, should be consise. Think post-it note, not paper.
7. Co-authors must be human. If you want to brag about your clanker,
   that does not belong in "Co-Authored-By:".
8. Don't use a clanker to write your commit messages. Show some
   (self-)respect. If you couldn't be bothered to write it, why should
   we be bothered to read it?

Code style
==========

Format the code with ruff, see the config in pyproject.toml. It is part of the
dependency group "dev".

A pre-commit hook will format new code automatically before committing.
To enable this pre-commit hook, run

::
    $ pre-commit install

Merge requests
==============

Small, please. Don't mix new functionality and refactors in the same
request.

"Missing" functionality should exist in "pyargus" first so that this remains
just a light wrapper.

Tests
=====

Yes, please. Unit tests only, pyargus tests the heavy stuff!
