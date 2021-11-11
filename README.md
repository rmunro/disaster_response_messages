# disaster_response_messages

## Summary
This dataset contains 20,000 messages drawn from events including an earthquake in Haiti in 2010, floods in Pakistan in 2010, super-storm Sandy in the U.S.A. in 2012, and news articles spanning a large number of years and 100s of different disasters. The data has been encoded with 38 different categories related to disaster response and has been stripped of messages with sensitive information in their entirety. 

## License

This dataset is released under creative commons attribution license.

I responded to these events as a disaster responder. For Haiti and Pakistan, I also looked at applying NLP to the datasets to understand how we could improve future disaster response efforts. This became part of my PhD thesis, which should be attributed when using this dataset:

Munro, Robert (2012). [Processing short message communications in low-resource languages](https://purl.stanford.edu/cg721hb0673). [PhD thesis, Stanford University]. Stanford Digital Repository. Retrieved from https://purl.stanford.edu/cg721hb0673


```
@phdthesis{phdthesis,
  author       = {Robert Munro}, 
  title        = {Processing short message communications in low-resource languages},
  school       = {Stanford University},
  year         = 2012,
  address      = {Stanford, CA},
  month        = 6,
  url         = {https://purl.stanford.edu/cg721hb0673}
}
```

See below for other early papers about this dataset that should be referenced for certain use cases.


## Categories

There are 38 categories, plus the messages themselves and (for Haiti only) the dates of the messages.

The categories are hierarchical, with sub-categories for `aid_related`, `infrastructure_related`, and `weather_related`.

1. id: Unique ID number for the messages. The IDs are in roughly the order that the messages were written.
2. split: `training`, `validation` or `test`
3. message: the English message
4. original: in the case of non-English messages in Haiti and Pakistan, the original message before translation
5. genre: `direct` or `news`
6. related: `0` or `1`, whether the message is related to a disaster 
7. PII:  `0` or `1`, whether the message is related to a disaster (all `0` in this public release)
8. request: `0` or `1`, whether the message is a request for aid
9. offer: `0` or `1`, whether the message is offering help
10. aid_related: `0` or `1`, whether the message is related to aid

    11. medical_help: `0` or `1`, whether the message is about medical help
    
    13. medical_products: `0` or `1`, whether the message is about medical products
    14. search_and_rescue: `0` or `1`, whether the message is about search and rescue
    15. security: `0` or `1`, whether the message is about personal security
    16. military: `0` or `1`, whether the message is about military actions
    17. child_alone: `0` or `1`, whether the message is about a child/children who are without adult care (all `0` in this public release)
    18. water: `0` or `1`, whether the message is about drinking water
    19. food: `0` or `1`, whether the message is about food
    20. shelter: `0` or `1`, whether the message is about shelter
    21. clothing: whether the message is about clothing
    22. money: whether the message is about money
    23. missing_people: whether the message is about missing people
    24. refugees: whether the message is about refugees or internally displaced people
    25. death: whether the message is about death
    26. other_aid: whether the message is about another aid-related topic
26. infrastructure_related: whether the message is about infrastructure-related issues
    27. transport: whether the message is about transport like buses, trains, planes, boats, taxis, bicycles, etc.
    28. buildings: whether the message is related to buildings: unstable, collapsed, inundated, usable as shelters, etc. 
    29. electricity: whether the message is related to power infrastructure, including public utilities and private generators
    30. tools: whether the message is about tools related to disaster prevention and response
    31. hospitals: whether the message is related to infrastructure for medical care, including hospitals and makeshift clinics 
    32. shops: whether the message is related to shops, markets, and other places of commerce, real or online
    33. aid_centers: whether the message is related to aid_centers
    34. other_infrastructure: whether the message is related to other types of disaster-related infrastructure
35. weather_related: whether the message is weather-related
    36. floods: whether the message is related to flooding
    37. storm: whether the message is related to storms, including hurricanes, tornadoes and snow-storms
    38. fire: whether the message is related to fire, including house fires and bush/forest fires
    39. earthquake: whether the message is related to earthquakes
    40. cold: whether the message is related to dangers from cold weather
    41. other_weather: whether the message is related to other weather events
42. direct_report: whether the message is a direct report from someone experiencing/witnessing the disaster or if they are reporting second/third hand
43. event: which event, `haiti_earthquake`, `pakistan_floods`, `usa_sandy`, or `NULL` for news
44. actionable_haiti: was this message considered something that could be responded to at the time? (Haiti only)
45. date_haiti: date the message was sent (Haiti only)


# Thanks

Thank you to the people who worked on Mission 4636 in Haiti and Pakreport in Pakistan who provided the translations and some of the categories. Thank you to Joan Xiao for helping with the identification and scrubbing of messages with sensitive or personal identifiable information (PII). 



Shield: [![CC BY 4.0][cc-by-shield]][cc-by]

This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg
