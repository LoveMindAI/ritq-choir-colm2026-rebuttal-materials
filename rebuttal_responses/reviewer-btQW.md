## Reviewer btQW
### Presenting CHOIR as a method, with the study as one application

Thank you for the review and for pointing out where the paper should be clearer about what CHOIR is as a framework, rather than only reporting the experiments built around it.

#### The core CHOIR loop

You noted that the submitted paper made it hard to tell which pieces are required parts of CHOIR and which are applications. We have prepared a boxed algorithm and flow chart for the camera-ready method clarification. In brief, CHOIR takes a question bank, model ensemble, prompt templates, and temperatures as input; elicits multiple ranked free lists per model/question/template/temperature; extracts one concept item per numbered list entry; clusters extracted items into a shared per-question codebook; computes concept salience using Smith's S; compares salience profiles across models using rank-biased overlap (RBO); and estimates signal-to-chance using a shuffle baseline. Persona conditioning and blind ranking will be labelled as applications demonstrated in this paper, not required parts of CHOIR.

#### Inventory, related work, and logprobs

You also asked for more justification and visibility around the question inventory. We will clarify that the inventory was not adapted from a single cognitive-anthropology survey and is not meant as a canonical benchmark. It was designed as a study instrument spanning several kinds of open-ended cognitive demand: social modelling, conversational memory, human welfare, computational self-description, meta-inquiry, and a high-consensus medication-safety control. The camera-ready supplement will include exact stems and representative examples so readers can judge the inventory directly rather than relying on labels such as "book recommendation intake." We will also clarify a count issue: the core CHOIR bank contains 26 questions, while the separate Q_PI persona-impact probe family is documented alongside it.

The camera-ready related-work paragraph will address the comparison you suggested. Work on diverse-perspective extraction and multilingual prompting asks how to elicit more diversity from a model. CHOIR asks a different diagnostic question: when multiple models appear to converge, is that convergence stable concept-level agreement, prompt-vocabulary echo, or shallow overlap? CHOIR is therefore not designed to maximise diversity; it measures which concepts remain stable under temperature and prompt perturbation, and which emerge only under deeper elicitation or conditioning.

Finally, on logprobs: the camera-ready version will add a short discussion explaining why logprobs and CHOIR are complementary rather than interchangeable. Logprobs are token-local and context-specific. CHOIR is concept-level and cross-provider: it asks which semantic items recur across samples, templates, temperatures, and models. Logprobs could help explain stability in open-weight models that expose them, but they are not available uniformly across the closed- and open-weight ensemble used here and therefore cannot replace the cross-model CHOIR analysis.

The camera-ready version will also add a compact research-question roadmap so each RQ is easier to read with its method, metric, result, interpretation, and limitation together, reducing the need to cross-reference between Methods and Results.

---
