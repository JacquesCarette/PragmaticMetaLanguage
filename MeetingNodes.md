## August 26, 2025, Spencer's notes

Conventions are an example of pragmatics.

We discussed examples of various conventions, like naming conventions, such as lower case letters from the beginning of the alphabet for parameters and lower case letters late in the alphabet for variables (like a*x^2 + b*x + c, rather than x*a^2 + y*a+z).  Other examples of conventions are f, g and h for function names, bold face for vectors, delta for change, etc.

JC said there are many other examples of pragmatics that we would have discussed in previous meetings.  I looked through my notes from previous meetings and the only other example I found was units.  I assume units are considered pragmatic because they aren’t necessary to form an expression.  They are extra information that we add to help us know the expression is meaningful.

JC proposed that maybe the semantics of the metalanguage can be given “implicitly” by its successful rendering into target languages, rather than specifying an inherent semantics.  WF pushed back that since we are only mapping to a core part of the language, rather than the entire language, specifying the semantics should be possible.  We then discussed how the semantics is feasible for mathematical expressions, and I believe feasible for (the relevant subset of) a programming languages, but natural language is where things get tricky.

For natural language artifacts we have the challenge of the structural choices for the document.  (Maybe this isn’t that challenging, since pandoc seems to have codified these options?) What goes in which section/subsection/paragraph etc. What is the order of the parts?  Table of contents at the end of the document is a choice that authors can make.  We also know more than the information in the table of contents.  We know the kind of information that goes in an introduction, in the conclusions, etc.  For instance, a common part of writing is a “roadmap” of the sections and subsections ahead.  This kind of roadmap should be something that we can generate.  We also have rendering choices, like hyperlinks within one big document, or hyperlinks to separate files, or a pdf file, or ...


## July 22, 2025, Jacques's notes

We need to remember that the 'original problem' that started these discussions might be phrased as follows:

Given a family of purposes (like programs, specifications, other narratives, tests, and so on), and for each of those a family of languages (so for programs, we could have Java and Python), we would like a meta-language in which we can 'say' everything we need so that we can view projecting out the data necessary for a purpose, in a particular language as just that, projection (or extraction).

Thus the needed information, modulo choices (such as notation) should already be present in the source. [This is why we don't want to reconstruct that a model is an ODE, rather the model should tell us that it's an ODE. The direction of information flow is important.]

We know that 'encoding' some of the needed information can be done with a theory network. We don't know how to *use* a theory network to "get the job done", i.e. how to meaningfully extract the information. Other information, such as that needed for specifications, narrative and tests, is not as obviously encodable in that way. That's another challenge.


## July 22, 2025, Spencer's notes

Question: Can we use Bill’s Little Theories in Drasil?
 
Answer: Yes, and No.  The little theories work well for the mathematical knowledge, but would not currently capture other information, like rationale, intent units, and documentation.  Jacques also mentioned that relevant information about the kind of a quantity is buried.  For instance, we want it to be obvious that a quantity is defined by an ODE.  We want this information “up front”.

We discussed the example of the different notation conventions for vectors, like bold face, arrow over vector symbol, underline of vector symbol, index notation.

We referred to the extra information that is necessary, but not typically captured by syntax and semantics, as pragmatics.  We discussed the example of units.

We concluded with the idea that we should build a list of the pragmatic information that people haven’t thought through.

## September 25, 2025, Summary of Meeting

As a step toward creating a pragmatic metalanguage, JC proposed first working on several example over languages, where an over language abstracts the syntax of several target (or under) languages so that programs written in the over language can generate code in each of their associated under languages. Once we have enough examples of over languages, we will likely need "over over" languages. When we understand things well enough, we can target a different kind of over language, which JC termed a multi-concern language.

Example of over languages include:

- GOOL (and GProc)
- pandoc
- the work in Drasil abstracting html and LaTeX (doclang?)
- typescript is an over language of Javascript
- LLVM (Low Level Virtual Machine) is an over language for assembly. LLVM serves as a common Intermediate Representation (IR). Frontends (like Clang) translate source code into LLVM IR. Backends then optimize the IR and generate machine code for different architectures (x86, ARM, RISC-V, etc.).
- JC's work with Reed on an over language for Agda/Lean/Idris/Rocq
- one could envision an over language for various logics that don't have good mutual-interpretability results but yet can still 'say' some of the same things. Maybe this is [Dedukti](https://deducteam.github.io/)?

JC observed that racket could be seen as a metalanguage for creating over languages.

Over languages focuses on syntax, but semantics sneaks in.  WF gave the example of universal quantification, which requires three elements: quantifier, variable, body. You need to be able to recognize the variable in the body.

WF mentioned that an over language could be used on top of a target language where one does not like the syntax of the target language.

An over language does not need all of the features of the under languages. This is one of the strengths of this approach. One gets to design both the over language and the translations. An over language may also contain linguistic features that are not present in any of the under languages (such as design patterns in GOOL) but must be 'elaborated away'.

Examples of different programming language targets where only one of the options is necessary:

- do while versus repeat until
- where and let 
- single let and multilet

Having such redundancy is useful for human comprehension but not for computational expressivity. But, being syntactic, this is an implicit admission that the principal stakeholders are humans rather than machines. Thus cognitive load is an important consideration.

## October 2, 2025, Summary of Meeting

- One of the challenges will be how to properly comment the "under" language code.  How do we attach things in the right spot in the under languages? That is, how do we put the English in the right spot and say the right thing?  For instance, the over language may have array expressions, but the under language is forced to use for loops.
- Potential paper title: Designing Syntactic Over Languages
    - a section that defines what an over language is
    - the body of the paper presents the design principles that we reverse engineer from the case studies
- Jacques gave the example of something that is not an over language. The example was generating sorting algorithms (Quick Sort) in many languages from Prolog to C. This is an example of an abstract language, not an over language.  The "distance" between the language and the generated code is greater for an abstract language than for an over language.
- An example of an over language principle is that quantification has 3 components

## October 23, 2025, Summary of Meeting

- the over language has to contain all the necessary language to cover all chosen under languages
- the translator must know the syntax for all under languages
- for example, if one of the under languages has types, the over language must also have types.  The type information would be ignored for those under languages that do not need it
- advantages of over language
    - we can design the syntax ourselves
    - we get to pick where we land in the under languages - we can pick the features that we use, and ignore those we do not want
- the mapping from the over language to the under language is not necessarily surjective, but it is necessarily injective
- the mapping does not have to be total
- our paper will not be on the theory of over languages but on the design of over languages.  We will need a definition of what an over language is
- homework - Spencer to examine GOOL as an over language, Bill to examine [Dedukti](https://deducteam.github.io/), Jacques to examine [Pandoc](https://pandoc.org/)

## October 30, 2025, Summary of Meeting

- will need a meta language, a language to discuss the languages
- we don't yet know where we will publish

## November 6, 2025, Summary of Meeting

- [Dedukti](https://deducteam.github.io/) is not really an over language.  It is a logical framework.  It serves a different purpose from an over language.
- a sentence in an over language has fundamental information + annotations.  When mapped to an under language the fundamental information should remain, but some annotations can be forgotten.
- if a sentence, s, in an over language maps to two sentences, s1 and s2 (in languages L1 and L2, respectively), than s1 "means the same as" s2.
- we currently have three over languages: pandoc, GOOL and panbench
- panbench is an over language for the structure of the syntax of 4 languages: [agda](https://en.wikipedia.org/wiki/Agda_(programming_language)), [idris](https://www.idris-lang.org/), [lean](https://lean-lang.org/) and [rocq](https://rocq-prover.org/). 
- we discussed how over languages are used.  An over language is an intermediate language.  The over language could be the target of a generator, as in the case of Drasil code generating GOOL code.  For pandoc, the normal use case is for translation.  A sentence s1 in language L1 could be translated to a sentence s in the over language, and then that sentence could be translated to a new sentence s1 in language L2.  For panbench the language is intended to be used directly to write tests.
- [rust](https://rust-lang.org/) is a typed, low-level language with ownership types.  JC mentioned that it can be considered as a modern replacement for C.
- WF said that it would be relatively easy to build an over language for first-order logic - a family of syntax of first order logics

## November 13, 2025, Summary of Meeting

- we discussed ["S2Doc - Spatial-Semantic Document Format" by Kempf and Puppe (2025)](https://arxiv.org/pdf/2511.01113) because it relates to our "big picture" goal of a pragmatic meta language
- in particular, we discussed Figure 1
which shows 6 views of the same table: the table itself, the physical view, the logical view, the functional view, the semantic view and the ontological view.
- HOMEWORK: review the two papers that are the inspiration for Kempf and Puppe (the third paper mentioned is the source of the example table):
   - [Xinxin Wang, 1996. Tabular Abstraction, Editing and Formatting, PhD Thesis, University of Waterloo.](https://cs.uwaterloo.ca/research/tr/1996/09/CS-96-09.pdf)
   - [Matthew Francis Hurst. 2000. The Interpretation of Tables in Texts. PhD Thesis, University of Edinburgh.](https://era.ed.ac.uk/handle/1842/7309)

- the design of an over language starts with the set of under languages plus the things you want to say in the over language.  The goal is not to say everything the under languages to say; the focus is narrowed to the things in the domain of interest.  For instance, GOOL code does not capture everything that can be said in Java, Python, C++ and C#; it captures the parts that are needed for the domain of scientific software programs.
- OCaml and Haskell look different because Ocaml doesn't have type classes.  However, the two language let you say more or less the same thing.
- To determine what subset of the under languages should be covered by the over language we look at what we want to say in our domain

## November 29, 2025, Summary of Meeting

- We discussed the two papers mentioned during the Nov 13 meeting (Wang, 1996 and Hurst 2000)
- We aren't interested in Hurst's specific goal of extracting information from table in documents.  His goal is to extract contents from a given table in a document for a natural language processing system.  Our goal is to capture data and generate a tabular view of this data.  We "know" the information already.  The challenge is the right way to capture it and the right way to visualize it.
- Horst's physical tables layer corresponds to the knowledge modelled by over languages like LaTeX, and html
- we could view the data in a table in tabular form, or in some cases, we could plot this data in a graph.  These are different views of the same knowledge.
- we can identify types of tables so that less low-level data is necessary.  For instance, Parnas tables have a variety of types (inverted table, normal table, decision table, vector table etc).  If we know the type of the table we only need to provide the data.  The visualization of the table is known, so we don't need the low level (physical level) details.
- we discusssed psycholinguistics (psychology + linguistics) because people bring an intuitive understanding to tables.  (As an aside, Smith recently had a discussion with Istvan about a graph of the prerequisite relation between our courses.  Smith put the first year courses on the bottom of the graph, but Istvan said people read from the top down, so the first year courses should be at the top.)
- Horst (2000) has a section on psycholinguistics.  In this section he introduces some other table types: list tables and matrix tables.
- people bring an intuitive understanding to tables
- we need at least two languages: 
1) language that encapsulates data
2) language of display
- this is analogous to XML (data) and CSC (display)
- we agreed that for our next meeting we would continue the discussion of Wang and Horst

## December 11, 2025, Summary of Meeting

- we had a brief conversation inspired from the Horst and Wang theses
- in our approach the table is a means of representation; it is not the primary artifact
- next week we plan to get back to discussing our plans for writing a paper

## December 18, 2026

- proposed paper structure:
   - examples
      - example around logics (Bill)
      - GOOL (Spencer)
      - pandoc (Jacques)
      - panbench (Jacques)
   - synthesis
   - principles

- [TPTP](https://tptp.org/UserDocs/TPTPLanguage/TPTPLanguage.shtml) - single format for first order logic

- [ACL2](https://en.wikipedia.org/wiki/ACL2) 
   - in the related literature we can discuss this language
   - many things can be translated into this language (not necessarily easy to read)
   - a language that expresses the meaning of other things - it is horrible for syntax
   - good language for machines, not for people - too verbose for people

- we discussed internal and external languages - over languages are eternal

- useful to create an overlanguage when we have a domain over which we want to say many things - there are many languages that can say what we want to say, but we don't want to choose
- there are many reasons to not choose 
- flexibility of choice is not needed when an ecosystem with one language does everything you need in a syntax that is fit for the purpose

- an interface language allows going from language A to B via the interface language - this is what pandoc does, and what LLVM does
- an interface language doesn't have to be something that humans look at

- our overlanguage concept includes interfaces, but is not limited to this use case

- pandoc doesn't really have a surface language {I assume we are using surface language to mean user-facing language.}

- where to publish?
   - we want people from many areas to look at the paper
   - we could try [Programming](https://programming-journal.org/) - joint journal and conference
   - International Joint Conference on Automated Reasoning [IJCAR](https://ijcar.org/)


   
