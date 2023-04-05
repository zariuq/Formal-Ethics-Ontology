# Formalization of Ethical Theory

This repository contains initial work on the formalization of ethical theory in the [SUMO ontology](https://github.com/ontologyportal/sumo) that was partially presented at [AITP](http://aitp-conference.org/2022/) as a 'project proposal'.

The idea is to develop precise definitions of ethics and the primary paradigms ([deontology](https://plato.stanford.edu/entries/ethics-deontological/), [virtue ethics](https://plato.stanford.edu/entries/ethics-virtue/), and [utilitarianism](https://plato.stanford.edu/entries/consequentialism/)) in a unifying framework (SUMO).  The framework will allow one to define particular theories within the paradigms (e.g., a particular set of ethical rules or utility functions one wishes to reason about).

To ensure the definitions are "good enough", crafting examples that one can reason with (such as via calls to theorem provers) is also important.  The classic Trolley problem is essentially an archetype underlying any multi-armed bandit scenario.  Moreover, with calls for ["Truthful LLMs"](https://twitter.com/elonmusk/status/1626533667408596992?s=20), formal specifications of truthfulness and honesty in the various paradigms may prove helpful.

For a casual exposition of my understanding of ethics, please see my blog post: [Virtue Ethics Qua Learning Theory](https://gardenofminds.art/blog/virtue-ethics/).  This study of ethics led to the conclusion that some interesting conjectures and applications require formal precision to advance.

SUMO is a pretty good language to use because _SUO-KIF_ is a fairly simple logic, and Adam Pease et al. have already defined 20,000+ concepts and 80,000+ theory statements that make describing "real world" ethical descriptions much easier.  Moreover, we might wish to export the ethics ontology from SUMO to another system such as OpenCog Hyperon's [MeTTa](https://arxiv.org/abs/2203.15970) for probabilistic or paraconsistent reasoning.  This may help in integrating the knowledge of ethical frameworks and value systems into the cognitive processes of an AGI system.

#### Contents of the Repository:

There is a classic _Organ Transplant_ dilemma where there are five dying patients and one healthy patient who could serve as a donor for them all.  The point is that in the _Trolley Problems_, people might intuitively choose to pull the lever to kill one and spare five, yet in this scenario, our intuition is that something's wrong with going to town -- what gives?

For simplicity, we settled on a scenario with only one dying patient and one healthy patient.  The ethical dilemma still exists.

The file "Transplant_Scenario_FO.kif" contains a description of the setting of the organ transplant dilemma.  I initially wished to involve reasoning such as the fact that "healthy primates have two kidneys", so requisitioning a kidney won't _kill_ the healthy patient (which should effect utility calculations 😏); however, due to lack of time I only defined that an "organ transplant" is a subclass of a "surgery" and that in this case the surgeon "will perform" the surgery given the right conditions. 

There are three "expository inferences" in a first-order form:

1) In the deontology case, the surgery happens when there is informed consent (and otherwise, there's no specification).

2) In the virtue ethics case, the surgery happens when there is consent, and the surgeon is practically wise (a virtue).

3) In the utilitarian case, the surgery happens if and only if the utility after the surgery is greater than the utility before the surgery.

The visual proofs are in the "Transplant_Proofs" directory.

Ideally, modal operators will be used so that "the surgeon is (ethically) permitted to perform the surgery in the case that informed consent from the healthy patient has been received".  SUMO can easily express this but the exports to a [TPTP](https://www.tptp.org/) format that theorem provers (namely [Vampire](https://vprover.github.io/)) use doesn't handle modal logic nor higher-order logic well [__yet__](http://aitp-conference.org/2022/abstract/AITP_2022_paper_18.pdf).  There are hacks to work around this in practice (to an extent).  Anyway, it's a cool minimal viable proof-of-concept.

I made a first pass at defining ethics within SUMO in May 2022 (found in the file "Ethics_Draft_1_May_2022.kif").  The initial attempt helped me to see what challenges may be involved.  Ethics is a field of study with subfields (.e.g., Moral Nihilism, Deontology, etc.).  Is ethics done in the context of a group of (cognitive) agents such as humans?  Can we use the deontic operators (of obligation, permission, prohibition, and rights), or do we need new "Normative Attributes" for moral good and bad?  (I think it's the latter.)  Moral Nihilism was the easiest "paradigm" to start with, followed by Deontology because it deals with "logical rules of ethics", and SUMO is a logical language.  The focus was on how the different schools make good/bad judgments.  The modern theorem provers don't seem to work with numbers very well, which might contribute to confusion as to how to represent "utility functions and associated aggregation functions" in SUMO.  There are also curious gems such as the  state of mind, "AppraisalOfPleasantness".  I defined some sketches of the classic Golden Rule, a prohibition on killing, what honest communication is and the virtue of truthfulness, and one idea as to the meaning of "epistemic universal love".

By the end, I realized the definitions would be cleaner if built around a notion of a "choice point": when can an agent be said to "have a choice to make"?  Ethical judgments are often done in the context of the options available (rather than on a one-off basis).  

I'm excited to start on the second pass of ontology formalization.  I wonder which examples will help to clarify how to frame the high-level definitions.  

Finally, I believe each ethical paradigm can embed the others.  In "Ethical_Paradigm_Equivalence_Outline.pdf", I outline how to embed deontology and utilitarianism within virtue ethics; utilitarianism and virtue ethics within deontology; and virtue ethics and deontology within utilitarianism.  I'm not sure how 'easy' a formal proof will be but I'd like to keep the idea in mind when formalizing.  And in the [Formal Abstracts](https://formalabstracts.github.io/) and ontology vein, formally specifying the conjecture is a start 😉🤓.  There is some support in the academic literature for the hypothesis, e.g., Martha Nussbaum's "[Virtue Ethics: A Misleading Category?](https://link.springer.com/article/10.1023/A:1009877217694)" where she notes that Kantianism and Utilitarianism deal with virtues.  [Utilitarianism](https://iep.utm.edu/util-a-r/) has arguably dealt with ethical rules since the days of John Stuart Mill, at least.

The presentation of this project proposal at the [AITP 2022 conference](http://aitp-conference.org/2022/http://aitp-conference.org/2022/) can be found in the file "Presentation: Formal Ethics in SUMO - AITP22.pdf". 

The extended abstract is in "Formal_Ethics_Ontology_Extended_Abstract.pdf".  This document includes a sketch of how the ethical paradigms might be expressed in a multi-agent reinforcement learning setting.

The second drafts are a living document: ethics_drafts_v2.kif.  

And the folder Ethics Kifs contains distinct files for the current best versions of the ethical paradigms, supporting definitions, and SUMO class declarations.

