<frontmatter>
  header: header.md
  pageNav: 2
  pageNavTitle: "Chapters of This Page"
  siteNav: site-nav.md
</frontmatter>

<br>

<div class="jumbotron jumbotron-fluid bg-primary text-white">
  <div class="container">
    <h1 class="display-4">MarkBind</h1>
    <p class="lead">Generate more dynamic websites from Markdown text</p>
  </div>
</div>

# Welcome to MarkBind
MarkBind source files can be as simple as basic Markdown, but you can also [**use a mix of several popular syntax schemes**](https://markbind.org/userGuide/markBindSyntax.html) (<tooltip content="GitHub Flavored Markdown">GFMD</tooltip>, BootStrap, NunJucks, etc. as well as MarkBind's own custom syntax) to create more dynamic content that you cannot normally get from a typical markdown-to-html site generator.

Here are some simple text-formatting examples:

Syntax scheme | Code | Output
--------------|------|-------
Markdown | `**bold text** _italic text_` | **bold text** _italic text_
GFMD | `~~striked out text~~` | ~~striked out text~~
MarkBind extensions to Markdown | `==highlighted text==`<br>`%%grey text%%`<br>`++underlined text++` | ==highlighted text==<br>%%grey text%%<br>++underlined text++

<box type="info"> This is the website we made specially for the demo. </box>


**What our demo includes:**

* An understanding of `markbind init`, `markbind build`, and `markbind serve` commands
* Live coding. We'll show you just how easy it is to work with MarkBind components and other syntax like - 
  1. Panels
  1. Embedding media
  1. Using `<include/>`, our killer feature
  1. PUML diagrams
* Working with plugins
* Subsites - what are they and how do I create one?
* Syntax you can use to create awesome websites
* Deploying your website

## Real-world examples 

**Here's an extract from the CS2103/T website-**

Given below is a summary of what the module CS2103/T covers and does not cover.

Topic | {{ icon_tick_green }} Covered | {{ icon_x_red }} Not covered
------|---------|------------
Java | Used heavily, but not taught | syntax %%(reason: expected prerequisite knowledge)%%
OOP | Used in a non-trivial project, <tooltip content="e.g., Single Responsibility Principle, Open-Closed Principle">intermediate OOP principles</tooltip> | basics %%(reason: expected prerequisite knowledge)%%
SE tools/practices | <tooltip content="e.g., revision control, continuous integration, practices, test automation, code reviews, pull requests">those typically used in a mature, high-rigor SE project</tooltip> | those specific to start-ups</md></td>
Modeling | <tooltip content="e.g., class diagrams, sequence diagrams, activity diagrams">Some UML notations</tooltip> (sufficient to be able to describe SE artifacts using models, such as seen in [this Developer Guide of AB3](https://se-edu.github.io/addressbook-level3/DeveloperGuide.html#design)) | intensive <tooltip content="creating detailed UML models before strating to code">upfront design modeling</tooltip>
Requirements | <tooltip content="e.g., user stories, use cases">Some lightweight techniques</tooltip> to gather and document project requirements | rapid prototyping, heavy UI design, designing a product from scratch
Documentation | Documentation targeting end users ([example](https://se-edu.github.io/addressbook-level3/UserGuide.html)) as well as those targeting developers ([example](https://se-edu.github.io/addressbook-level3/DeveloperGuide.html)) | Marketing materials
Project Management | Iterative delivery of a product, working collaboratively with team members, on-site as well as remotely | Setting up project infrastructure from scratch
Testing | <tooltip content="e.g., automated unit/integration/system testing">basic developer testing</tooltip> and <tooltip content="e.g., acceptance testing">user testing</tooltip> | <tooltip content="e.g., security testing, performance testing, usability testing">testing for non-functional aspects</tooltip>
Applications domains | Cross-platform desktop applications | Web programming, Mobile programming, Database programming


## Media Embeds

**Video embed:**

@[youtube](https://www.youtube.com/watch?v=ttrNjqT9KJc)

**Tabs:**

<tabs>
  <tab header="Tab X">
    Some text some text some text some text some text some text some text. Some text some text some text some text some text some text some text. Some text some text some text some text some text some text some text some text some text some text some text some text some text some text. Some text some text some text some text some text some text. Some text some text some text some text some text some text some text.
  </tab>
  <tab header="Tab Y">
    ...
  </tab>
  <tab-group header="Tab group">
    <tab header="Tab Y.1">
      ...
    </tab>
    <tab header="Tab Y.2">
      ...
    </tab>
  </tab-group>
</tabs>

<br>

# Showcasing our boxes

**Some boxes:**

<box>
    default
</box>
<box type="info">
    info
</box>
<box type="warning" dismissible>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
</box>
<box type="tip" heading="Tip box heading">
    tip
</box>
<box type="success" heading="Tip box heading">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
</box>
<box type="important" dismissible heading="Tip box heading">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
</box>

<br>

# Showcasing our panels (killer feature)

<panel header="Click here to learn about primitive data types" type="info">

  * Boolean, true or false.
  * Character
  * Floating-point, single-precision real number values.
  * Double, a wider floating-point size.
  * Integer, integral or fixed-precision values.
  * String, a sequence of characters.
  * Reference (also called a pointer or handle), a small value referring to another object's address in memory, possibly a much larger one.
  * Enumerated type, a small set of uniquely named values.

%%<sub>[source:wikipedia]</sub>%%
</panel>
<br>

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
<panel header="___Minimal panel **->**___" type="minimal" alt="Minimal panel" popup-url="https://markbind.org/userGuide/usingComponents.html#panels" no-switch>
Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</panel>

Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

<box type="success">
    That's all, folks!!!
</box>