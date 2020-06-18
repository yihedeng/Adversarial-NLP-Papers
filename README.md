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

### __Word-level Attack__ 
Modifying (replacing) words in a given input sequence to achieve an attack.
- [Word-level Textual Adversarial Attacking as Combinatorial Optimization](https://arxiv.org/pdf/1910.12196.pdf). Yuan Zang, Fanchao Qi, Chenghao Yang, Zhiyuan Liu, Meng Zhang, Qun Liu, Maosong Sun. ACL 2020.
  - [...]

- [Seq2Sick: Evaluating the Robustness of Sequence-to-Sequence Models with Adversarial Examples](https://arxiv.org/pdf/1803.01128.pdf). Minhao Cheng, Jinfeng Yi, Pin-Yu Chen, Huan Zhang, Cho-Jui Hsieh
  - _white-box_ attack targetting __seq2seq__ models.
  - Focusing on nonoverlapping attack and targeted keywords attack.
    - Nonoverlapping attack: generated adversarial exmaples do not share overlapping word with the original sentence.
    - Targeted keywords attack: given a set of targeted keywords, the adversarial examples must contain all of the keywords.
  - Perturbations made on the word embedding space under the additional attack constraints.
  - The word in dictionary that has the closest embedding distance to the computed adversarial embedding is selected for replacement.
  - Similar to other white-box gradient-based methods, seq2sick is fast in computation. However, as the author noted, the difficulty lies in converting the adversarial embedding back to a valid word token.

- [Generating Natural Language Adversarial Examples through Probability Weighted Word Saliency](https://www.aclweb.org/anthology/P19-1103.pdf) Shuhuai Ren, Yihe Deng, Kun He, Wanxiang Che. ACL 2019.
  - Similarly _black-box_ word-level attack method based on synonym substituiton.
  - Proposing the Probability Weighted Word Saliency (PWWS) method that greedily makes word substitution.
  - The synonym for replacement is determined by the combined score of _word saliency_ and class confidence change.
    - Word saliency: the change of the model's confidence when the specific word is set to unknown.

- [Generating Natural Language Adversarial Examples](https://www.aclweb.org/anthology/D18-1316.pdf). Moustafa Alzantot, Yash Sharma, Ahmed Elgohary, Bo-Jhang Ho, Mani Srivastava, Kai-Wei Chang. EMNLP 2018.
  - Proposing a _black-box_ word-level attack method based on __synonym substituiton__.
  - Using a genetic algorithm to iteratively evolve a population of candidate adversarial examples for a sentence toward better perturbations.
  - A more detailed review of this paper can be found __[[here](https://medium.com/@lilydeng/literature-review-generating-natural-language-adversarial-examples-a8727ea6c30e)].__
    
### __Combined Attack__
Combining the perturbation methods from above for an adversarial attack
- [Deep Text Classification Can be Fooled](https://www.ijcai.org/Proceedings/2018/585). Bin Liang, Hongcheng Li, Miaoqiang Su, Pan Bian, Xirong Li, Wenchang Shi. IJCAI, 2018.
  - Using _insertion, modification, and removal_: (1) inserting __Hot Training Phrases__ (HTPs); (2) modifying __Hot Sample Phrases__ (HSPs) with its common typos or visually similar phrases; (3) removing inessential adjective or adverb from HSPs.
  - Introducing the natural language watermarking technique to decide what to insert, modify or remove, where to insert and how to modify.
  - Proposing methods for both _white-box_ and _black-box_ settings.
  
### __Sentence-level Attack__
- [Adversarial Example Generation with Syntactically Controlled Paraphrase Networks](https://www.aclweb.org/anthology/N18-1170.pdf). Mohit Iyyer, John Wieting, Kevin Gimpel, Luke Zettlemoyer. NAACL-HLT, 2018.
  - Proposing __syntactically controlled paraphrase networks__ (SCPNs) for attack based on backtranslation.
  - Generating paraphrases for the input sentence to achieve adversarial attack.
  
- [Semantically Equivalent Adversarial Rules for Debugging NLP models](https://www.aclweb.org/anthology/P18-1079.pdf). Marco Tulio Ribeiro, Sameer Singh, Carlos Guestrin. ACL, 2018.
  - Introducing __semantically equivalent adversaries__ (SEAs) and generalizing these adversaries to __semantically equivalent adversarial rules__ (SEARs).
    - SEARs represent the set of generalized rules (substituting a specific word with another, for example) that produce adversaries for any input sentence.
  - Achieves global attack: SEARs can be easily applied to different tasks and sentences.
