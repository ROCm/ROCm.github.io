# Contributing to ROCm

Thank you for your interest in contributing to ROCm! There are many ways to
contribute, and we appreciate all of them. This document is a bit long, so here's
links to the major sections:

* [Feature Requests](#feature-requests)
* [Bug Reports](#bug-reports)
* [Pull Requests](#pull-requests)
* [Writing Documentation](#writing-documentation)
* [Issue Triage](#issue-triage)


## Feature Requests

To request a change to the way that the ROCm Platform, it's language or libraries works, please open an
issue in the [RFCs repository](https://github.com/RadeonOpenCompute/rfcs/issues)
rather than this one. New features and other significant changes
need to go through the RFC process.

## Bug Reports

The fun part of software admitting we not perfect, if you see an issue please report it only way we can make ROCm better. 

If you have the chance, before reporting a bug, please [search existing
issues](https://github.com/RadeonOpenCompute/ROCm/issues),
as it's possible that someone else has already reported your error.

Opening an issue is as easy as following [this
link](https://github.com/RadeonOpenCompute/ROCm/issues/new) and filling out the fields.
Here's a template that you can use to file a bug, though it's not necessary to
use it exactly:

    <Summary of your hardware:CPU,GPU,WHich PCIe lane your GPU are inserted>
    
    <short summary of the bug>

    I tried this:

    <code sample that causes the bug>

    I expected to see this happen: <explanation>

    Instead, this happened: <explanation>

    ROCm,  HIP, HCC, OpenCL,
    
    OS Distro and Version 
    

## Pull Requests

Pull requests are the primary mechanism we use to change ROCm. GitHub itself
has some [great documentation][pull-requests] on using the Pull Request
feature. We use the 'fork and pull' model described there.

[pull-requests]: https://help.github.com/articles/using-pull-requests/

Please make pull requests against the `master` branch.

All pull requests are reviewed by our team. 

After someone has reviewed your pull request, they will merge the request.

## Writing Documentation

Documentation improvements are very welcome.  Documentation pull requests function in the same way as other pull requests. 

To find documentation-related issues, sort by the [Bug_Documentation label][Bug_Documentation].

[Bug_Documentation ]: https://github.com/RadeonOpenCompute/ROCm/labels/Bug_Documentation

We are currently working on our documentation style guidelines, are open to suggestions. 

The documentation system we are using for the project is Sphinx based. We 

All documentation can writtern Markdown or reStructuredText  

[Master Documentation Project Source Repository](https://github.com/RadeonOpenCompute/ROCm_Documentation)

## Issue Triage <Section under development>

Sometimes, an issue will stay open, even though the bug has been fixed. And
sometimes, the original bug may go stale because something has changed in the
meantime.

It can be helpful to go through older bug reports and make sure that they are
still valid. Load up an older issue, double check that it's still true, and
leave a comment letting us know if it is or is not. The [least recently
updated sort][lru] is good for finding issues like this.

Contributors with sufficient permissions on the ROCm repo can help by adding
labels to triage issues:

* Yellow, **A**-prefixed labels state which **area** of the project an issue
  relates to.

* Magenta, **B**-prefixed labels identify bugs which are **blockers**.

* Green, **E**-prefixed labels explain the level of **experience** necessary
  to fix the issue.

* Red, **I**-prefixed labels indicate the **importance** of the issue. The
  [I-nominated][inom] label indicates that an issue has been nominated for
  prioritizing at the next triage meeting.

* Orange, **P**-prefixed labels indicate a bug's **priority**. These labels
  are only assigned during triage meetings, and replace the [I-nominated][inom]
  label.

* Blue, **T**-prefixed bugs denote which **team** the issue belongs to.

* Dark blue, **beta-** labels track changes which need to be backported into
  the beta branches.

* The purple **metabug** label marks lists of bugs collected by other
  categories.

If you're looking for somewhere to start, check out the [E-easy][eeasy] tag.

