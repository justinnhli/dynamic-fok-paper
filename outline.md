# Towards a Computational Model of a Feeling of Knowing

# introduction

* what is FOK
* brief of existing psychology theories
    * accessibility
    * cue familiarity
* no existing models in a cognitive architecture?

# situating within a strategic knowledge search framework

* "[meta]cognitive-heuristic account of metacognitive judgments"
    * [Schwartz2011TipOfThe] offers both psychological and neuro-imaging evidence for the cognitive-heuristic account, at least for TOTs
* memory as a strategic process
    * knowledge search (Newell1972HumanProblemSolving)
    * "the Control of Recollection" ([Burgess1996ConfabulationAndThe])
* metamemory ([Nelson1990MetamemoryATheoretical])
    * part of metamemory monitoring
    * could be part of search strategy selection and search termination
* information foraging theory (Pirolli2007InformationForagingTheory)
    * mostly addresses *external* sources of knowledge
    * no conception of search strategy
    * comparison with information scent
* potential roles of FOK from <https://justinnhli.com/papers/h/Hanczakowski2014FeelingOfKnowing.pdf>
    * could be used for control as well as monitoring, as it was found that FOK influences restudy choices
    * FOKs may replace JOLs after failed a recall attempt
* what is the difference between "study time" and "test time" when it comes to JOL versus FOK?
* FIXME
    * Deliberate FOK versus automatic FOK
* FIXME
    * [Nelson2008TowardsARational]

# what is the role of FOK?

* necessary even without forgetting, since knowledge may not be there
* determined that cost doesn't matter to FOK, history of retrievals does (but not to our model), and history of FOK is important to FOK and our model
* as conclusion from memory frameworks, FOK should be dynamic
* separate from search cost, from confidence of answer, from base "utility"/activation
* we differentiated between steps so far and queries so far but did not use queries so far since all of our retrievals only used one query, but now we are using multiple retrieval strategies if one fails/ multiple queries can be done for one retrieval, so maybe this is worth looking into?
* potential uses of FOK from [Hanczakowski2014FeelingOfKnowing]
    * could be used for control as well as monitoring, as it was found that FOK influences restudy choices
    * FOKs may replace JOLs after failed a recall attempt
        * the difference between these is unclear, and there mere separation of "at study time" versus "at retrieval time" seems arbitrary - does study not require retrieval for testing?
* evidence that FOK is correlated with search termination reaction time if "don't know" ([Singer2008FeelingOfKnowing])
    * in fact, termination RT is correlated with familiarity with topic

# Modeling Framework

* ACT-R, flat buffers, etc.
* parameter to choose whether things are activated on store or not
    * when did this make a difference?
* adding a huge number of nodes to kb (unrelated or related to queries)

# methodological outline

* three questions from [Koriat1993HowDoWe]
    1. How accurate is FOK?
    2. How is FOK produced?
    3. How does Q2 account for Q1?
* 12 mechanisms from [Nelson1984AccuracyOfFeeling]
    * Trace-access mechanisms
        * Subthreshold strength
        * Forward-backward associations
        * Correct semantic referent but no label
        * Partial recall of label
            * both of the above are related to partial retrieval
        * Wrong referent
        * Multidimensional target
    * Inferential mechanisms
        * Related episodic information
        * Recognition of cue
        * Claimed related episodic information
        * Expertise on topics
        * Actuarial information
        * Social desirability
            * the last four here might be related to Schwartz2014ContextualInformationInfluences
            * in that they are usual contextual knowledge
* pre- and post-retrieval accounts ([Florer2000FeelingsOfKnowing]) muddled in dynamic FOK
    * borrowing from TOT research, question of whether the same retrieval failure process leads to FOK, or if it's a post-hoc diagnostic process ([Schwartz2011TipOfThe])

# FOK related work

* recognition
    * literature
        * "trace-based view" in [Koriat1993HowDoWe]
            * consulting an index first; see [Li2012FunctionalInteractionsBetween]
        * considered pre-retrieval in Florer2000FeelingsOfKnowing
            * unclear how this is different from cue-familiarity in that paper
    * example
        * FIXME
    * possible models
        * see [Li2012FunctionalInteractionsBetween]
* accessibility of pertinent information
    * literature
        * "accessibility" in [Koriat1993HowDoWe]
            * "These include activations from the terms in the question; structural, contextual, and semantic attributes; fragments of the target; and so on."
                * importantly, these are "parasitic" (ie. a side effect) of retrieval itself
                * they exist even if the retrieval itself fails
            * "The cues that are used in computing FOK during a retrieval attempt can be classified into two types, those that have to do with the accessibility of information pertaining to the target and those that are based on the specific content of the information accessed. The term accessibility will be used here to subsume two major cues: the amount of information activated or accessed and its intensity (e.g., its ease of access, vividness, specificity, and persistence). [...] In other cases, however, the subject may be able to evaluate the content of the information recovered, pitting different clues against each other and making de- liberate, educated inferences about the plausibility that the solicited target will be subsequently recalled or recognized. This may sometimes be the case with real-world knowledge, particularly at the later stages of retrieval."
            * however, can be super broad:
                * capitals of similar/related countries
                * partial retrievals
                * incorrect retrievals
        * as intra-retrieval account of FOK in [Florer2000FeelingsOfKnowing]
            * in contrast to pre-retrieval FOK, as in recognition/cue-familiarity
            * manipulate accessibility/retrieval correctness via Ranschburg effect
                * where strings with repeated letters (RFKXFNL) are recalled less accurately than strings without (RFKXBNL)
    * example
        * FIXME
    * possible models
        * hard to say, given broadness
            * Koriat classifies it as an "inferential mechanism"; may not be a simple signal?
            * also hints at dynamic nature - by definition, depends on what results have come back, and will change over time
* cue familiarity
    * literature
        * used as first step before accessibility
            * multiple sources (both Koriat)
                * [Koriat1993HowDoWe]
                * [Koriat2001TheCombinedContributions]
            * makes sense from a computational perspective: cue familiarity is cheap and should be used as a gate
        * considered pre-retrieval in Florer2000FeelingsOfKnowing
            * unclear how this is different from recognition in that paper
    * Bryce's notes
        * experiment results contradict competition hypothesis ([Schreiber1998TheRelationBetween])
        * (I need to reread this because I'm not sure how it's different from Koriat's 1993 paper above also discussing accessibility)
    * example
        * FIXME
    * possible models
        * activation
            * rationale: base-level activation determines how recently and frequent an item is used, hence "familiar" with it
        * fan in/out/all
            * rationale: amount of associated knowledge with that item
* speed of progress towards goal
    * ex: how quickly could you come up with a country's capital? (did multiple strategies have to be used because some failed?)
* number of potential matches
    * ex: when thinking of a country's capital, how many different possible cities come to mind?
* number of potential next elements (fan out)
    * FIXME how is this different from number of potential matches?
* inverse of the number of distractors (competition FOK) [Schreiber1998TheRelationBetween]
    * experimental results that show FOK is inversely correlated with number of relevant facts
        * paper goes into detail about types of facts that contribute to this
        * acknolwedges that both "partial-retrieval" and competition plays a role
            * separates cue recognition as third thing, since experiments can use made-up words
    * may be related to bias variance tradeoff?
        * that is, if a relevant facts hints at other competing answers, descrease FOK
        * slightly different from what was proposed in the paper: not just type of fact, but its relation to possible answers as well
    * ex: when thinking of a country's capital, if you know many large cities that could be the capital, the one you decide to go with is unlikely to be correct given the large number of possibilities you have.
* number of values associated with a certain concept (outgoing edges from cue)
    * ex: when asked to name the capital of a country, the more you know about that country in general, the more likely it is that you know the capital.
* amount of info known about a result compared to everything else in memory
    * mention using average activation (or other summary statistics)
    * ex: when thinking of a country's capital, how well do you know the city you are thinking of compared to everything else you know?

# complex/ conjugate features of FOK

* starting with computational and trying to explain it in psychological terms
* (explain in graph theory and try to create explanations)
* cue activation * total edges (didn't work)
    * trying to apply Koriat (1993) idea of "The term accessibility.... subsume[s] two major cues: the amount of information activated or accessed and its intensity"
    * ex: when thinking of a country's capital, how much information do you know about the country and how strongly do you know it?
* average of cue and target activations (didn't use?)
    * ex: when naming a country's capital, how well do you know the country and how well do you know the possible answer you are currently thinking of?
* cue activation * number of outgoing edges of cue
    * (the same as cue act * total edges except only looks at outgoing edges rather than incoming and outgoing)
    * how to explain that out edges is different than total edges in terms of example??
* activation of target * number of outgoing edges of target
    * ex: when asked to name a country's capital, how much information do you know about the city you are thinking of and how strongly do you know it?
* activation over edges: log of current ratio of activation to edges divided by avg ratio of activation to edges
    * ex: when thinking of a country's capital, given the number of things you know about the city you are currently thinking of, how well do you know this city? (doesn't really make sense, like how well it is known per piece of information known about it)

# dynamic features of FOK

* past FOKs?
* used different FOK calculations based on where in the retrieval process the FOK occurred (using one method for a query and another method for subsequent retrievals)

# TOT states
<https://justinnhli.com/papers/s/Schwartz2011TipOfThe.pdf>
* approaches to understanding TOT:
    * direct access view - something blocks retrrieval so that the activation of the target is high enough to cause a TOT state, but too low for recall
    * two-step view - TOT may come from partial rather than failed retrievals and TOT states may indicate higher activation of target instead of just a failed retrieval
    * heuristic-metacognitive account - focuses on what information is used to get to the TOT state, even information that is not directly related to the target (for example, syntactic and phonemic information, emotion)
* past attempts at retrieving a target may influence TOT

# Partial Knowledge
<https://justinnhli.com/papers/n/Norman2016TheRelationshipBetween.pdf>
* past studies exploring the relationship between FOK and partial knowledge have measured FOK after retrieval of partial knowledge
* this study measured FOK before a partial knowledge retrieval and found that FOK is still influenced by partial knowledge before it's recalled
* FOKs are experience-based rather than just a measurement of retrieval speed or amount of partial information
* correct partial knowledge was a predictor of FOK, while incorrect partial knowledge was not
    * FOK increased with the amount of correct partial knowledge and the existence of incorrect partial knowledge

# Related Work

* (Unhelpful?) FOK related work
    * [Nelson1984AccuracyOfFeeling]
        * lists twelve potential mechanisms for FOK in the discussion
        * proposed alternate methods of measuring the accuracy of FOK
            * note: procedure is recall, FOK, measure, so may not be relevant for argument of dynamic FOK
        * instead of recognition as metric, proposed:
            * perceptual identification (based on pre-experimental history of participant)
            * relearning
        * results
            * perceptual identification and relearning were found to not differ greatly in the rates of how search for non recalled answers is determined by what people feel they know rather than what they know
            * FOK is also reliable predictor of relearning
    * [Widner1996TheEffectsOf]
        * on whether you're willing to admit you don't know
            * indeed, the high-demand condition led to more tip-of-the-tongue states
        * confidence: related to expectation of difficulty?
        * expectation of ease of retrieval affecting FOK?
        * study on "easy" vs "difficult" questions
* computational KB work
    * [Sharma2016ControllingSearchIn]
        * learning a heuristic for inference; uses similar features as what we consider below
    * [Salvucci2015EndowingACognitive]
        * an ACT-R DBpedia paper we read, talks about triplet and chunk representations?

# evaluation metrics

* unclear what FOK should look like, for queries with and without answers
* need big dataset of questions and KB for evaluation?
* we claimed that FOK should be increasing when the correct answer is reached (positive slope), should decrease as you get farther from the correct answer, and should decrease when you give up
    * but is this necessarily true? we found that changes in FOK over time heavily depended on the individual question
    * examples:
        * Lanyard Question: "You may use this item whose name comes from sailing terminology to keep track of your college dorm key"
            * FOK should be high at first ("i know about college!")
            * then should lower as nothing is found for college and holds key, lowers as nothing is found for sailing and hold key, and is quite low (with a negative slope) by the time it finds lanyard, even though that is the correct answer
        * Olympics Washington Question: "What is the capital of the nation that is hosting a major international sporting event in 2028?"
            * FOK should start off high since multiple international sporting events are known, Euro cup is guessed incorrectly and FOK lowers, and it continues to lower until the correct location is found, then FOK increases once it is looking at LA because of the amount of knowledge it has of LA (here it actually increases when finding the answer)
        * Marapi Question:
            * for all FOK calculations except for one (outgoing edges FOK), FOK decreases as the answer is found (we had so many different retrieval steps for this question that i'm not even sure what FOK pattern we were expecting/ looking for)
* unidirectional search vs multi-directional search

-----

# Bryce's unorganized notes of progress made over the summer

* recreated Liebert and Nelson's paired recall task, made 3 different representations (direct, pairs, types)
* since there is no standard for calculating FOK, we recreated some basic ones (cue/ target familiarity)
* wanted to look at more complex retrievals with more steps and with more information in the kb to test FOK algorithms, so we coded up Jeopardy Qs
* created historic FOK (trend based)

Parameters we held constant:
* `act_decay_rate` = [-0.25]
* `act_scale_factor` = [0.5]
* `act_max_steps` = [30]
* `act_capped` = [True]
* `backlinks` = [True]

maybe unrelated things we mentioned that still seem interesting:
* looking at distance between different cues given to determine how likely you are to get an answer
* how to broaden a query/ how to factor in what the next, less-direct query is? ex. how would the agent know that a capital is often a large city
* free association? other than creating edges called `related_to` ?

# Related work:

* [Li2016ArchitecturalMechanismsFor] Justin's 2016 paper on "Architectural Mechanisms for Mitigating Uncertainty during Long-Term Declarative Knowledge Access"

# Psychology Studies:

* [DeSoto2014PositiveAndNegative] correlation between confidence and accuracy
    * This study sought to resolve seemingly contradicting results from previous experiments involving the correlation between confidence and accuracy in recall tests. Subjects were presented with 12 short lists of words in 12 different categories. Then they took a yes/no recognition test over a larger set of items: 1/3 the studied words (targets) from the previous task, 1/3 "related lures" (unstudied words from the same 12 categories), and 1/3 "unrelated lures" from new categories. Subjects indicated whether they believed each item to be studied or unstudied, then rated their confidence in this recognition decision on a scale from 0 to 100.
    * Results: 70-73% correct for targets
    * 28-39% false alarms for related lures
    * 10% false alarms for unrelated lures
* [Hanczakowski2017MetamemoryInA]
    * experiments that assess role of factors that shape FOK judgments
    * Experiment 1: investigations of context effects in recognition
        * Involves participants studying cue-target pairs of words presented w/ photos
        * Next cued-recall test, participants presented w/ cues and asked to retrieve photo targets
        * Provide FOK judgments for all cues
        * Cued recall performance best in reinstated context condition
    * Experiment 2: same as above but also pre familiarized context condition (context familiarity manipulated through pre-exposure procedure used in previous FOG judgments)
        * Preexposure phase, participants were presented w/ individual BW photographs, an asked about pleasantness
        * Participants were presented with targets with distractor words
        * Cue used for targets in recognition trial
        * Found that reinstating context benefits cued-recall performance
            * But be careful to keep context familiarity equal
    * Results:
        * FOK judgments were influenced by context familiarity, with later recognition of unrecalled targets
        * Higher predictions of later recognition due to context reinstatement
* [Schwartz2014ContextualInformationInfluences]
    * (Oxy doesn't grant access, but I have a PDF of it)
    * Experiment:
        * Participants were each shown a number of made-up creatures that were accompanied with varying levels (there were three different levels) of contextual information. For example, some creatures would only have a name listed, some would have name and country of origin, and some would have name, country, diet, and weight. FOKs were measured for identifying both the animal given context, and context given animal.
    * Results:
        * Participants had higher FOKs for retrieving animals that came with more context (second two levels). This makes sense because of spreading activation, if any of the given animals shared traits. Also, if country and diet were not made up places/ things, they might have some activation already from before the experiment.
    * Made up animals represent new information that a person doesn't have any context for, despite the size or contents of their knowledge base. - So, adding context for each animal creates entirely new nodes and edges that would not have been referenced before. (ie. if country and diet were also made up things)


[Burgess1996ConfabulationAndThe]: https://justinnhli.com/papers/b/Burgess1996ConfabulationAndThe.pdf
[DeSoto2014PositiveAndNegative]: https://justinnhli.com/papers/d/DeSoto2014PositiveAndNegative.pdf
[Florer2000FeelingsOfKnowing]: https://justinnhli.com/papers/f/Florer2000FeelingsOfKnowing.pdf
[Hanczakowski2014FeelingOfKnowing]: https://justinnhli.com/papers/h/Hanczakowski2014FeelingOfKnowing.pdf
[Hanczakowski2017MetamemoryInA]: https://justinnhli.com/papers/h/Hanczakowski2017MetamemoryInA.pdf
[Koriat1993HowDoWe]: https://justinnhli.com/papers/k/Koriat1993HowDoWe.pdf
[Koriat2001TheCombinedContributions]: https://justinnhli.com/papers/k/Koriat2001TheCombinedContributions.pdf
[Li2012FunctionalInteractionsBetween]: https://justinnhli.com/papers/l/Li2012FunctionalInteractionsBetween.pdf
[Li2016ArchitecturalMechanismsFor]: https://justinnhli.com/papers/l/Li2016ArchitecturalMechanismsFor.pdf
[Mangan2000WhatFeelingIs]: https://justinnhli.com/papers/m/Mangan2000WhatFeelingIs.pdf
[Nelson1984AccuracyOfFeeling]: https://justinnhli.com/papers/n/Nelson1984AccuracyOfFeeling.pdf
[Nelson1990MetamemoryATheoretical]: https://justinnhli.com/papers/n/Nelson1990MetamemoryATheoretical.pdf
[Nelson2008TowardsARational]: https://justinnhli.com/papers/n/Nelson2008TowardsARational.pdf
[Salvucci2015EndowingACognitive]: https://justinnhli.com/papers/s/Salvucci2015EndowingACognitive.pdf
[Schreiber1998TheRelationBetween]: https://justinnhli.com/papers/s/Schreiber1998TheRelationBetween.pdf
[Schwartz2011TipOfThe]: https://justinnhli.com/papers/s/Schwartz2011TipOfThe.pdf
[Schwartz2014ContextualInformationInfluences]: https://justinnhli.com/papers/s/Schwartz2014ContextualInformationInfluences.pdf
[Sharma2016ControllingSearchIn]: https://justinnhli.com/papers/s/Sharma2016ControllingSearchIn.pdf
[Widner1996TheEffectsOf]: https://justinnhli.com/papers/w/Widner1996TheEffectsOf.pdf
