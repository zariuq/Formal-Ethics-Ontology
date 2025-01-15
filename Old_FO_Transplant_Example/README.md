This example was done in the start of the project and was not continued to the current drafts (which are more sophisticated in terms of formal definition technology).

#### Contents of the Repository:

There is a classic _Organ Transplant_ dilemma where there are five dying patients and one healthy patient who could serve as a donor for them all.  The point is that in the _Trolley Problems_, people might intuitively choose to pull the lever to kill one and spare five, yet in this scenario, our intuition is that something's wrong with going to town -- what gives?

For simplicity, we settled on a scenario with only one dying patient and one healthy patient.  The ethical dilemma still exists.

The file "Transplant_Scenario_FO.kif" contains a description of the setting of the organ transplant dilemma.  I initially wished to involve reasoning such as the fact that "healthy primates have two kidneys", so requisitioning a kidney won't _kill_ the healthy patient (which should effect utility calculations 😏); however, due to lack of time I only defined that an "organ transplant" is a subclass of a "surgery" and that in this case the surgeon "will perform" the surgery given the right conditions. 

There are three "expository inferences" in a first-order form:

1) In the deontology case, the surgery happens when there is informed consent (and otherwise, there's no specification).

2) In the virtue ethics case, the surgery happens when there is consent, and the surgeon is practically wise (a virtue).

3) In the utilitarian case, the surgery happens if and only if the utility after the surgery is greater than the utility before the surgery.

The visual proofs are as named.

Ideally, modal operators will be used so that "the surgeon is (ethically) permitted to perform the surgery in the case that informed consent from the healthy patient has been received".  SUMO can easily express this but the exports to a [TPTP](https://www.tptp.org/) format that theorem provers (namely [Vampire](https://vprover.github.io/)) use doesn't handle modal logic nor higher-order logic well [__yet__](http://aitp-conference.org/2022/abstract/AITP_2022_paper_18.pdf).  There are hacks to work around this in practice (to an extent).  Anyway, it's a cool minimal viable proof-of-concept.
