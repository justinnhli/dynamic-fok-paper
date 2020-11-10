# Towards a Computational Model of a Feeling of Knowing

## introduction

* what is FOK
* brief of existing psychology theories
    * accessibility
    * cue familiarity
* no existing models in a cognitive architecture?

## situating within a strategic knowledge search framework

* memory as a strategic process
    * knowledge search (Newell1972HumanProblemSolving)
    * "the Control of Recollection" (https://justinnhli.com/papers/b/Burgess1996ConfabulationAndThe.pdf)

* metamemory (https://justinnhli.com/papers/n/Nelson1990MetamemoryATheoretical.pdf)
    * part of metamemory monitoring
    * could be part of search strategy selection and search termination

* information foraging theory (Pirolli2007InformationForagingTheory)
    * mostly addresses *external* sources of knowledge
    * no conception of search strategy
    * comparison with information scent

* FIXME
    * https://justinnhli.com/papers/n/Nelson2008TowardsARational.pdf

## what is the role of FOK?

* necessary even without forgetting, since knowledge may not be there

* determined that cost doesn't matter to FOK, history of retrievals does (but not to our model), and history of fok is important to FOK and our model

* as conclusion from memory frameworks, FOK should be dynamic

* separate from search cost, from confidence of answer, from base "utility"/activation

* we differentiated between steps so far and queries so far but did not use queries so far since all of our retrievals only used one query, but now we are using multiple retrieval strategies if one fails/ multiple queries can be done for one retrieval, so maybe this is worth looking into?

## FOK related work

* fluency/ accessibility approach to FOK
    * How Do We Know What We Know? Asher Koriat 1993: http://iipdm.haifa.ac.il/images/publications/Asher_Koriat/1993-Koriat-PR%20FOK.pdf
    * "two stage" explanation of FOK: initial FOK is based on cue-familiarity and subsequent FOKs are based on accessibility
    * According to Koriat, subsequent FOKs only occur after an incorrect answer is given, at the beginning of a new retrieval attempt. There is no mention of multiple FOKs occurring within a single retrieval.
        * So, he is not saying that FOK is dynamic but rather that one FOK occurs for every attampted retrieval in a retrieval process (i think??)

* accessibility and cue familiarity
    * https://iipdm.haifa.ac.il/images/publications/Asher_Koriat/2001-KorLevySadot-JEPLMC.pdf
    * the accessibility and cue familiarity hypotheses for FOK are not mutually exclusive, but rather two distinct processes that contribute to overall FOK separately
    * experiment results contradict competition hypothesis
    * (i need to reread this because I'm not sure how it's different from koriat's 1993 paper above also discussing accessibility)

## modeling framework

* ACT-R, flat buffers, etc.

* parameter to choose whether things are activated on store or not
    * when did this make a difference?

* adding a huge number of nodes to kb (unrelated or related to queries)

## static features of FOK (FIXME need references for all of these)

* for each one, review psychology literature
    * then map onto ACT-R model and what that might look like

* accessibility
    * FIXME

* cue familiarity (activation)
    * FIXME In our notes, we have cue familiarity = outgoing edges from cue and accessibility being activation

* speed of progress towards goal
    * ex: how quickly could you come up with a country's capital? (did multiple strategies have to be used because some failed?)

* number of potential matches
    * ex: when thinking of a country's capital, how many different possible cities come to mind?

* number of potential next elements (fan out)
    * FIXME how is this different from number of potential matches?

* inverse of the number of distractors (competition fok)
    * Schreiber & Nelson https://link.springer.com/content/pdf/10.3758/BF03201170.pdf
    * ex: when thinking of a country's capital, if you know many large cities that could be the capital, the one you decide to go with is unlikely to be correct given the large number of possibilities you have.

* number of values associated with a certain concept (outgoing edges from cue)
    * ex: when asked to name the capital of a country, the more you know about that country in general, the more likely it is that you know the capital.

* amount of info known about a result compared to everything else in memory
    * mention using average activation (or other summary statistics)
    * ex: when thinking of a country's capital, how well do you know the city you are thinking of compared to everything else you know?

## complex/ conjugate features of fok

* starting with computational and trying to explain it in psychological terms
* (explain in graph theory and trye to create explanations)

* cue activation * total edges (didn't work)
    * trying to apply Koriat (1993) idea of "The term accessibility…. subsume[s] two major cues: the amount of information activated or accessed and its intensity"
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

## dynamic features of FOK

* past FOKs?

* used different FOK calculations based on where in the retrieval process the FOK occurred (using one method for a query and another method for subsequent retrievals)

## Related Work

* (Unhelpful?) FOK related work
    * http://cogprints.org/7586/1/Mangan_2000_FeelingOfKnowing_ConsciousnessAndCognition.pdf
    * discusses TOT and responds to others' work, nothing very useful here
    * (many of the unhelpful works found were phychology studies rather than just papers about FOK)

* computational KB work

    * https://justinnhli.com/papers/s/Sharma2016ControllingSearchIn.pdf
        * learning a heuristic for inference; uses similar features as what we consider below

    * https://justinnhli.com/papers/s/Salvucci2015EndowingACognitive.pdf
        * an ACT-R DBpedia paper we read, talks about triplet and chunk representations?

## evaluation metrics

* unclear what FOK should look like, for queries with and without answers
* need big dataset of questions and KB for evaluation?
* we claimed that FOK should be increasing when the correct answer is reached (positive slope), should decrease as you get farther from the correct answer, and should decrease when you give up
    * but is this necessarily true? we found that changes in FOK over time heavily depended on the individual question
    * examples:
        * Lanyard Question: “You may use this item whose name comes from sailing terminology to keep track of your college dorm key”
            * FOK should be high at first ("i know about college!")
            * then should lower as nothing is found for college and holds key, lowers as nothing is found for sailing and hold key, and is quite low (with a negative slope) by the time it finds lanyard, even though that is the correct answer
        * Olympics Washington Question: "What is the capital of the nation that is hosting a major international sporting event in 2028?"
            * fok should start off high since multiple international sporting events are known, Euro cup is guessed incorrectly and fok lowers, and it continues to lower until the correct location is found, then fok increases once it is looking at LA because of the amount of knowledge it has of LA (here it actually increases when finding the answer)
        * Marapi Question:
            * for all FOK calculations except for one (outgoing edges fok), FOK decreases as the answer is found (we had so many different retrieval steps for this question that i'm not even sure what fok pattern we were expecting/ looking for)

* unidirectional search vs multidirectional search

## other human contextual effects

    confidence: related to expectation of difficulty?
    expectation of ease of retrieval affecting FOK?

-----

# bryce's unorganized notes of progress made over the summer

* recreated Liebert and Nelson's paired recall task, made 3 different representations (direct, pairs, types)
* since there is no standard for calculating fok, we recreated some basic ones (cue/ target familiarity)
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

## Related work:

* https://justinnhli.com/papers/l/Li2016ArchitecturalMechanismsFor.pdf Justin's 2016 paper on "Architectural Mechanisms for Mitigating Uncertainty during Long-Term Declarative Knowledge Access"

## Psychology Studies:

* http://www.jstor.org/stable/24540139 correlation between confidence and accuracy
    * This study sought to resolve seemingly contradicting results from previous experiments involving the correlation between confidence and accuracy in recall tests. Subjects were presented with 12 short lists of words in 12 different categories. Then they took a yes/no recognition test over a larger set of items: ⅓ the studied words (targets) from the previous task, ⅓ “related lures” (unstudied words from the same 12 categories), and ⅓ “unrelated lures” from new categories. Subjects indicated whether they believed each item to be studied or unstudied, then rated their confidence in this recognition decision on a scale from 0 to 100.

    * Results: 70-73% correct for targets
    * 28-39% false alarms for related lures
    * 10% false alarms for unrelated lures

* https://search-proquest-com.oxy.idm.oclc.org/docview/614333827?accountid=12935
* Nelson & Narens 1984
    * Tested two tests of FOK:
        * -perceptual identification (based on pre-experimental history of participant)
        * -relearning
    * Participants presented questions then answers to the questions

    * Methods:
    * Participants were asked to answer general questions such as what is the biggest planet in the solar system?
    * Their judgement of whether they would know the correct answer or not are tracked
    * Feeling of knowing judgements are ranked

    * Findings:
        * -perceptual identification and relearning were found to not differ greatly in the rates of how search for non recalled answers is determined by what people feel they know rather than what they know
        * -relearning experiment showed that FOK is also reliable predictor of relearning

* https://search-proquest-com.oxy.idm.oclc.org/docview/1794829606?accountid=12935
* experiments that assess role of factors that shape FOK judgements
    * Experiment 1: investigations of context effects in recognition
        * Involves participants studying cue-target pairs of words presented w/ photos
        * Next cued-recall test, participants presented w/ cues and asked to retrieve photo targets
        * Provide FOK judgements for all cues
        * Cued recall performance best in reinstated context condition

    * Experiment 2: same as above but also pre familiarized context condition (context familiarity manipulated through preexposure procedure used in previous FOK judgements)
        * Preexposure phase, participants were presented w/ individual BW photographs, an asked about pleasantness
        * Participants were presented with targets with distractor words
        * Cue used for targets in recognition trial
        * Found that reinstating context benefits cued-recall performance
            * But be careful to keep context familiarity equal
    * Results:
        * FOK judgements were influenced by context familiarity, with later recognition of unrecalled targets
        * Higher predictions of later recognition due to context reinstatement

* https://www.sciencedirect.com/science/article/abs/pii/S1053810014001561
* (Oxy doesn't grant access, but I have a PDF of it)
    * Experiment:
        * Participants were each shown a number of made-up creatures that were accompanied with varying levels (there were three different levels) of contextual information. For example, some creatures would only have a name listed, some would have name and country of origin, and some would have name, country, diet, and weight. FOKs were measured for identifying both the animal given context, and context given animal.

    * Results:
        * Participants had higher FOKs for retrieving animals that came with more context (second two levels). This makes sense because of spreading activation, if any of the given animals shared traits. Also, if country and diet were not made up places/ things, they might have some activation already from before the experiment.

    * Made up animals represent new information that a person doesn’t have any context for, despite the size or contents of their knowledge base. - So, adding context for each animal creates entirely new nodes and edges that would not have been referenced before. (ie. if country and diet were also made up things)
