# Disaster Response Messages

## Summary
This dataset contains 25,000 messages drawn from events including an earthquake in Haiti in 2010, floods in Pakistan in 2010, super-storm Sandy in the U.S.A. in 2012, and news articles spanning a large number of years and 100s of different disasters. The data has been encoded with 38 different categories related to disaster response and has been stripped of messages with sensitive information in their entirety. 

## License

This dataset is released under creative commons attribution license (see below). Please cite:

Robert Munro. 2012. [Processing short message communications in low-resource languages](https://purl.stanford.edu/cg721hb0673). [PhD dissertation, Stanford University]. _Stanford Digital Repository_. Retrieved from https://purl.stanford.edu/cg721hb0673

```
@phdthesis{munro12dissertation,
  author       = {Robert Munro}, 
  title        = {Processing short message communications in low-resource languages},
  school       = {Stanford University},
  year         = 2012,
  address      = {Stanford, CA},
  month        = 6,
  url         = {https://purl.stanford.edu/cg721hb0673}
}
```

I responded to these events as a disaster responder and for Haiti and Pakistan, I also looked at applying NLP to the datasets to understand how we could improve future disaster response efforts. This became part of my PhD thesis, which should be cited when using this dataset. See below for other early papers about this dataset that can be referenced for certain use cases.


## Categories

There are 38 categories, plus the messages themselves and (for Haiti only) the dates of the messages.

The categories are hierarchical, with sub-categories for `aid_related`, `infrastructure_related`, and `weather_related`.

* id: Unique ID number for the messages. The IDs are in roughly the order that the messages were written.
* split: `training`, `validation` or `test`
* message: the English message
* original: in the case of non-English messages in Haiti and Pakistan, the original message before translation
* genre: `direct` message or `news` headline
* related: `0`, `1` or `2`, whether the message is related to a disaster (`1` == yes, `1` == unsure)
* PII:  `0` or `1`, whether the message is related to a disaster (all `0` in this public release)
* request: `0` or `1`, whether the message is a request for aid
* offer: `0` or `1`, whether the message is offering help
* aid_related: `0` or `1`, whether the message is related to aid

    * medical_help: `0` or `1`, whether the message is about medical help
    * medical_products: `0` or `1`, whether the message is about medical products
    * search_and_rescue: `0` or `1`, whether the message is about search and rescue
    * security: `0` or `1`, whether the message is about personal security
    * military: `0` or `1`, whether the message is about military actions
    * child_alone: `0` or `1`, whether the message is about a child/children who are without adult care (all `0` in this public release)
    * water: `0` or `1`, whether the message is about drinking water
    * food: `0` or `1`, whether the message is about food
    * shelter: `0` or `1`, whether the message is about shelter
    * clothing: `0` or `1`, whether the message is about clothing
    * money: `0` or `1`, whether the message is about money
    * missing_people: `0` or `1`, whether the message is about missing people
    * refugees: `0` or `1`, whether the message is about refugees or internally displaced people
    * death: `0` or `1`, whether the message is about death
    * other_aid: `0` or `1`, whether the message is about another aid-related topic
    
* infrastructure_related: `0` or `1`, whether the message is about infrastructure-related issues

    * transport: `0` or `1`, whether the message is about transport like buses, trains, planes, boats, taxis, bicycles, etc.
    * buildings: `0` or `1`, whether the message is related to buildings: unstable, collapsed, inundated, usable as shelters, etc. 
    * electricity: `0` or `1`, whether the message is related to power infrastructure, including public utilities and private generators
    * tools: `0` or `1`, whether the message is about tools related to disaster prevention and response
    * hospitals: `0` or `1`, whether the message is related to infrastructure for medical care, including hospitals and makeshift clinics 
    * shops: `0` or `1`, whether the message is related to shops, markets, and other places of commerce, real or online
    * aid_centers: `0` or `1`, whether the message is related to aid_centers
    * other_infrastructure: `0` or `1`, whether the message is related to other types of disaster-related infrastructure
    
* weather_related: whether the message is weather-related

    * floods: `0` or `1`, whether the message is related to flooding
    * storm: `0` or `1`, whether the message is related to storms, including hurricanes, tornadoes and snow-storms
    * fire: `0` or `1`, whether the message is related to fire, including house fires and bush/forest fires
    * earthquake: `0` or `1`, whether the message is related to earthquakes
    * cold: `0` or `1`, whether the message is related to dangers from cold weather
    * other_weather: `0` or `1`, whether the message is related to other weather events
    
* direct_report: `0` or `1`, whether the message is a direct report from someone experiencing/witnessing the disaster or if they are reporting second/third hand
* event: which event, `haiti_earthquake`, `pakistan_floods`, `usa_sandy`, or `NULL` for news
* actionable_haiti: `0`, `1` or `NULL`, was this message considered something that could be responded to at the time? (Haiti only)
* date_haiti: `(YYY-MM-DD)` or `null', the date the message was sent (Haiti only)

# Data 

The data is split into training, validation, and test datasets:
* disaster_response_messages/blob/main/disaster_response_training.csv](https://github.com/rmunro/disaster_response_messages/blob/main/disaster_response_training.csv)
* [disaster_response_messages/blob/main/disaster_response_validation.csv](https://github.com/rmunro/disaster_response_messages/blob/main/disaster_response_validation.csv)
* [disaster_response_messages/disaster_response_test.csv](https://github.com/rmunro/disaster_response_messages/blob/main/disaster_response_test.csv)

The splits are random.

## Sources

The data from Haiti and Pakistan are SMS messages sent to disaster reporting services following the respective disasters in 2010. The data from Superstorm Sandy ("hurricane Sandy") are postings from a disaster-related message board in 2011. The news headlines are from approximately the same time periods and cover a much large set of disasters. 

All datasets are a subset of larger datasets that contains locations for some of the messages here and additional messages with sensitive and personal identifiable information that cannot be shared opely. This is why "PII" is `0` for all the data here. For access to more data from Haiti, including the chats between the people annotating the data, researchers working under IRB or equivalent can apply here: [https://www.mission4636.org/access-to-data/](https://www.mission4636.org/access-to-data/). Because of the sensitivity of messages related to children alone and the ethics regarding data that could be used to train a model to identify at-risk minors, no data about children alone is available in this dataset (or the ones available under IRB). This is why "child_alone" is `0` for all the data here.

To decide which data to open source, we used two sources. We ran a survey of people who took part in the disaster response efforts from among the disaster-affected communities and asked them what they felt to be appropriate data to share and what was sensitive. We also took the best practices in data protection globally, using GDPR as the basis for definitions of personally identifying and sensitive data. Where the two did not line up, we took the most conservative option of the two, keeping more data private.

There was only one case where we decided to be more careful than the majority vote. The majority people said that it was ok to remove sensitive information from the messages, but still share them with that information removed. However, enough people believed that the entire message should be omitted in this case, so we omitted the _entire_ message in the case that it contained sensitive data.

An earlier public release of this dataset contained about 5,000 additional messages from social media platforms at the time. These are omitted from these datasets as being the victim of a disaster is considered health-related. It is now standard that social media platforms do not allow health-related information to be encoded about public social media posts without a person's explicit consent, because the public social media messages can be searched and tied back to that person's identity. 

## Restrictions

The data should not be combined with other data such that it would reveal the identities of people sending or mentioned in the messages. If any message is found to still contain personally identifying information it should be excluded from your study. Please contact me in these cases so that it can also be removed from the datasets (my email is my github handle, @alumni.stanford.edu).

## Annotations

The data was annotated by a combination of paid and volunteer people who are native speakers of the original languages and in many cases were also victims of the disasters. See my dissertation and the "Crowdsourcing and the crisis-affected community" article below for more information.

# Common tasks

There are several common tasks that are meaninful for this dataset:

### Classification (all fields)

Multilabel classification for the 36 fields from "related" to "direct_report" and "actionable_haiti" (minus the always `0` "PII" and "child_alone".

### Classification (top level fields)

Multilabel classification for the 4 fields, "related", "aid_related", "infrastructure_related", and "weather_related".

### Intent Classification

Classification for the "request" and "offer" fields, which can be multilabel or recast as a multiclass problem "request", "offer", "both", "none".

### Eyewitness Report Identification

Classification for "direct_report"

### Actionable Information Detection

Classification for "actionable", for the Haiti data only. This is the task in 2011 ConLL paper below.

### Machine Translation

The Haiti and Pakistan data can be used to train and evaluate machine translation models. Note that some of translations are summaries/paraphrases and contain exposition by the translators, so some data cleaning might be needed.

A subset of the data was used as part of the shared task for the [2011 Workhop on Machine Translation (WMT)](https://www.statmt.org/wmt11/). See the WMT paper below for more details.

### Progressive Classification & Active Learning

An alternative to the random training/validation/test split is to split by time (dates for Haiti data and increasing IDs for the Pakistan data), training on earlier messages and predicting on later ones for the same disasters.

This is closer to a real-life situation. In the case that a subset of messages get a human label, this can be cast as an active learning task. This was how the problem was framed in my PhD and the 2011 ConLL paper below.

### Comparisons and transfer learning across domains

The distribution of information across the disasters and genres can be investigated. This can be purely analytical or it can also investigate transfer learning to adapt models from one domain to another, and the issues that might arise in these cases. This was how the problem was framed in our ACM DEV paper below.

# Acknowledgements

Thank you to the people who worked on Mission 4636 in Haiti and Pakreport in Pakistan who provided the translations and some of the categories. Thank you to Joan Xiao for helping with the identification and scrubbing of messages with sensitive or personal identifiable information (PII). 


# References

In additional to citing the PhD dissertation above, consider citing these papers when relevant to your task. They are mostly condensed versions of parts of my dissertation, so they are also quicker places to read first:

### Human translation and annotation of data during disaster response efforts:

Robert Munro. 2013. Crowdsourcing and the crisis-affected community - Lessons learned and looking forward from Mission 4636. _Journal of Information Retrieval_. 16:2. Springer.


```
@article{munro13crisis,
  author    = {Robert Munro},
  title     = {Crowdsourcing and the crisis-affected community - Lessons learned and looking forward from Mission 4636},
  journal   = {Journal of Information Retrieval},
  volume    = {16},
  number    = {2},
  pages     = {210--266},
  year      = {2013},
  publisher = {Springer}
}
```

### Identifying "actionable" data in the Haiti messages:

Robert Munro. 2011. Subword and Spatiotemporal Models for Identifying Actionable Information in Haitian Kreyol. _Proceedings of the Fifteenth Conference on Computational Natural Language Learning (CoNLL 2011)_. Association for Computational Linguistics.

```
@inproceedings{munro11conll,
  author    = {Robert Munro},
  title     = {Subword and Spatiotemporal Models for Identifying Actionable Information in \{H\}aitian \{K\}reyol},
  booktitle = {Fifteenth Conference on Computational Natural Language Learning ({CoNLL 2011})},
  pages     = {68--77},
  publisher = {Association for Computational Linguistics},
  year      = {2011}
}
```

### Comparing the categories across disasters and using transfer learning for domain adaptation from one disaster to another:

Robert Munro and Christopher D. Manning. 2012. Short message communications: users, topics, and in-language processing. _Proceedings of the Second Annual Symposium on Computing for Development (ACM DEV)_. Association for Computational Machinery.

```
@inproceedings{munro12acmdev,
  author    = {Robert Munro and
               Christopher D. Manning},
  title     = {Short message communications: users, topics, and in-language processing},
  booktitle = {Second Annual Symposium on Computing for Development ({ACM DEV})},
  pages     = {4:1--4:10},
  publisher = {Association for Computational Machinery},
  year      = {2012}
}
```


### Cross-lingual information extraction:

Robert Munro and Christopher D. Manning. 2012. Accurate Unsupervised Joint Named-Entity Extraction from Unaligned Parallel Text. _Proceedings of the 4th Named Entities Workshop (NEWS)_. Association for Computational Linguistics.

```
@inproceedings{munro12ner,
  author    = {Robert Munro and
               Christopher D. Manning},
  title     = {Accurate Unsupervised Joint Named-Entity Extraction from Unaligned Parallel Text},
  booktitle = {The 4th Named Entities Workshop (NEWS)},
  pages     = {21--29},
  publisher = {Association for Computational Linguistics},
  year      = {2012}
}
```

### Machine translation:

William Lewis, Robert Munro and Stephan Vogel. 2011. Crisis MT: Developing A Cookbook for Machine Translation in Crisis Situations. _Proceedings of the 6th Annual Workshop on Machine Translation (WMT@EMNLP)_. Association for Computational Linguistics.


```
@inproceedings{lewis11wmt,
  author    = {William Lewis and Robert Munro and Stephan Vogel},
  title     = {Crisis {MT:} Developing {A} Cookbook for Machine Translation in Crisis Situations},
  booktitle = {6th Annual Workshop on Machine Translation ({WMT@EMNLP})},
  pages     = {501--511},
  publisher = {Association for Computational Linguistics},
  year      = {2011}
}
```

# License

Shield: [![CC BY 4.0][cc-by-shield]][cc-by]

This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg
