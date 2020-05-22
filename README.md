# Papers in Adversarial Attack and Defense for NLP Tasks
Papers that I read through when doing related projects and research in the area, with summaries I wrote for easier reference

*Another useful repository of must read papers on textual adversarial attack and defense: https://github.com/thunlp/TAADpapers*

## Attacks: Generating Adversarial Examples in NLP
The attack methods are categorized by their different approach of perturbing an input sequence, based on my understanding. Since many methods adopts multiple types of perturbations, I categorize them by the majority/main type of their perturbations.
### __Character-level Attack__
Modifying characters in a given input sequence to achieve an attack.
- [TEXTBUGGER: Generating Adversarial Text Against Real-world Applications](https://www.ndss-symposium.org/wp-content/uploads/2019/02/ndss2019_03A-5_Li_paper.pdf). Jinfeng Li, Shouling Ji, Tianyu Du, Bo Li and Ting Wang. NDSS 2019.
  - Introducing TEXTBUGGER, an attack method that finds important words and considers mostly character-level perturbations with some word-level perturbation. 
  - Pertubations include (1) inserting a space into the word; (2) deleting a random character in the middle of the word; (3) swapping random two adjacent letters within a word; (4) replacing characters with visually similar characters or typos; (5) _[word-level]_ replacing the word with its top k nearest neighbors in the word vector space.
  - Proposing attack methods under both _white-box_ and _black-box_ settings.

- [HotFlip: White-Box Adversarial Examples for Text Classification](https://www.aclweb.org/anthology/P18-2006.pdf). Javid Ebrahimi, Anyi Rao, Daniel Lowd, Dejing Dou. ACL 2018. 
  - Proposing a _white-box_ adversarial attack targetting a character-level model.
  - Using atomic flip operation that swaps one token for another as the way of perturbation.
  - Additionally, they show that HotFlip can be adapted to word-level attacks. However, they could not generate abundant adversarial examples on word-level using HotFlip,
    - "These examples, albeit interesting and intuitive, are not abundant, and thus pose less threat to an NLP word-level model. Specifically, given the strict set of constraints, we were able to create only 41 examples (2% of the correctly-classified instances of the SST test set) with one or two flips."

### __Combined Attack__
Combining the perturbation methods from above for an adversarial attack
- [Deep Text Classification Can be Fooled](https://www.ijcai.org/Proceedings/2018/585). Bin Liang, Hongcheng Li, Miaoqiang Su, Pan Bian, Xirong Li, Wenchang Shi. IJCAI, 2018.
  - Using _insertion, modification, and removal_: (1) inserting __Hot Training Phrases__ (HTPs); (2) modifying __Hot Sample Phrases__ (HSPs) with its common typos or visually similar phrases; (3) removing inessential adjective or adverb from HSPs.
  - Introducing the natural language watermarking technique to decide what to insert, modify or remove, where to insert and how to modify.
  - Proposing methods for both _white-box_ and _black-box_ settings.
