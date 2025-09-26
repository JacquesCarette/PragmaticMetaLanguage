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
- one could envision an over language for various logics that don't have good mutual-interpretability results but yet can still 'say' some of the same things. Maybe this is Dedukti?

JC observed that racket could be seen as a metalanguage for creating over languages.

Over languages focuses on syntax, but semantics sneaks in.  WF gave the example of universal quantification, which requires three elements: quantifier, variable, body. You need to be able to recognize the variable in the body.

WF mentioned that an over language could be used on top of a target language where one does not like the syntax of the target language.

An over language does not need all of the features of the under languages. This is one of the strengths of this approach. One gets to design both the over language and the translations. An over language may also contain linguistic features that are not present in any of the under languages (such as design patterns in GOOL) but must be 'elaborated away'.

Examples of different programming language targets where only one of the options is necessary:

- do while versus repeat until
- where and let 
- single let and multilet

Having such redundancy is useful for human comprehension but not for computational expressivity. But, being syntactic, this is an implicit admission that the principal stakeholders are humans rather than machines. Thus cognitive load is an important consideration.
