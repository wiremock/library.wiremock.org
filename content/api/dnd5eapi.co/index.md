---
slug: "dnd5eapi-co"
title: "D&D 5e API"
provider: "dnd5eapi.co"
description: "# Introduction\n\nWelcome to the dnd5eapi, the Dungeons & Dragons 5th\
  \ Edition API!\nThis documentation should help you familiarize yourself with the\
  \ resources\navailable and how to consume them with HTTP requests. Read through\
  \ the getting\nstarted section before you dive in. Most of your problems should\
  \ be solved\njust by reading through it.\n\n## Getting Started\n\nLet's make our\
  \ first API request to the D&D 5th Edition API!\n\nOpen up a terminal and use [curl](http://curl.haxx.se/)\
  \ or [httpie](http://httpie.org/)\nto make an API request for a resource. You can\
  \ also scroll through the\ndefinitions below and send requests directly from the\
  \ endpoint documentation!\n\nFor example, if you paste and run this `curl` command:\n\
  ```bash\ncurl -X GET \"https://www.dnd5eapi.co/api/ability-scores/cha\" -H \"Accept:\
  \ application/json\"\n```\n\nWe should see a result containing details about the\
  \ Charisma ability score:\n```bash\n{\n  \"index\": \"cha\",\n  \"name\": \"CHA\"\
  ,\n  \"full_name\": \"Charisma\",\n  \"desc\": [\n    \"Charisma measures your ability\
  \ to interact effectively with others. It\n      includes such factors as confidence\
  \ and eloquence, and it can represent\n      a charming or commanding personality.\"\
  ,\n    \"A Charisma check might arise when you try to influence or entertain\n \
  \     others, when you try to make an impression or tell a convincing lie,\n   \
  \   or when you are navigating a tricky social situation. The Deception,\n     \
  \ Intimidation, Performance, and Persuasion skills reflect aptitude in\n      certain\
  \ kinds of Charisma checks.\"\n  ],\n  \"skills\": [\n    {\n      \"name\": \"\
  Deception\",\n      \"index\": \"deception\",\n      \"url\": \"/api/skills/deception\"\
  \n    },\n    {\n      \"name\": \"Intimidation\",\n      \"index\": \"intimidation\"\
  ,\n      \"url\": \"/api/skills/intimidation\"\n    },\n    {\n      \"name\": \"\
  Performance\",\n      \"index\": \"performance\",\n      \"url\": \"/api/skills/performance\"\
  \n    },\n    {\n      \"name\": \"Persuasion\",\n      \"index\": \"persuasion\"\
  ,\n      \"url\": \"/api/skills/persuasion\"\n    }\n  ],\n  \"url\": \"/api/ability-scores/cha\"\
  \n}\n```\n\n## Authentication\n\nThe dnd5eapi is a completely open API. No authentication\
  \ is required to query\nand get data. This also means that we've limited what you\
  \ can do to just\n`GET`-ing the data. If you find a mistake in the data, feel free\
  \ to\n[message us](https://discord.gg/TQuYTv7).\n\n## GraphQL\n\nThis API supports\
  \ [GraphQL](https://graphql.org/). The GraphQL URL for this API\nis `https://www.dnd5eapi.co/graphql`.\
  \ Most of your questions regarding the GraphQL schema can be answered\nby querying\
  \ the endpoint with the Apollo sandbox explorer.\n\n## Schemas\n\nDefinitions of\
  \ all schemas will be accessible in a future update. Two of the most common schemas\
  \ are described here.\n\n### `APIReference`\nRepresents a minimal representation\
  \ of a resource. The detailed representation of the referenced resource can be retrieved\
  \ by making a request to the referenced `URL`.\n```\nAPIReference {\n  index   \
  \  string\n  name      string\n  url       string\n}\n```\n<hr>\n\n### `DC`\nRepresents\
  \ a difficulty check.\n```\nDC {\n  dc_type       APIReference\n  dc_value     \
  \ number\n  success_type  \"none\" | \"half\" | \"other\"\n}\n```\n<hr>\n\n### `Damage`\n\
  Represents damage.\n```\nDamage {\n  damage_type     APIReference\n  damage_dice\
  \     string\n}\n```\n<hr>\n\n### `Choice`\nRepresents a choice made by a player.\
  \ Commonly seen related to decisions made during character creation or combat (e.g.:\
  \ the description of the cleric class, under **Proficiencies**, states \"Skills:\
  \ Choose two from\tHistory, Insight, Medicine, Persuasion, and\tReligion\" [[SRD\
  \ p15]](https://media.wizards.com/2016/downloads/DND/SRD-OGL_V5.1.pdf#page=15))\n\
  ```\nChoice {\n  desc      string\n  choose    number\n  type      string\n  from\
  \      OptionSet\n}\n```\n<hr>\n\n### `OptionSet`\nThe OptionSet structure provides\
  \ the options to be chosen from, or sufficient data to fetch and interpret the options.\
  \ All OptionSets have an `option_set_type` attribute that indicates the structure\
  \ of the object that contains the options. The possible values are `options_array`,\
  \ `equipment_category`, and `reference_list`. Other attributes on the OptionSet\
  \ depend on the value of this attribute.\n- `options_array`\n  - `options` (array):\
  \ An array of Option objects. Each item in the array represents an option that can\
  \ be chosen.\n- `equipment_category`\n  - `equipment_category` (APIReference): A\
  \ reference to an EquipmentCategory. Each item in the EquipmentCategory's `equipment`\
  \ array represents one option that can be chosen.\n- `resource_list`\n  - `resource_list_url`\
  \ (string): A reference (by URL) to a collection in the database. The URL may include\
  \ query parameters. Each item in the resulting ResourceList's `results` array represents\
  \ one option that can be chosen.\n<hr>\n\n### `Option`\nWhen the options are given\
  \ in an `options_array`, each item in the array inherits from the Option structure.\
  \ All Options have an `option_type` attribute that indicates the structure of the\
  \ option. The value of this attribute indicates how the option should be handled,\
  \ and each type has different attributes. The possible values and their corresponding\
  \ attributes are listed below.\n- `reference` - A terminal option. Contains a reference\
  \ to a Document that can be added to the list of options chosen.\n  - `item` (APIReference):\
  \ A reference to the chosen item.\n- `action` - A terminal option. Contains information\
  \ describing an action, for use within Multiattack actions.\n  - `action_name` (string):\
  \ The name of the action, according to its `name` attribute.\n  - `count` (number\
  \ | string): The number of times this action can be repeated if this option is chosen.\n\
  \  - `type` (string = `\"melee\" | \"ranged\" | \"ability\" | \"magic\"`, optional):\
  \ For attack actions that can be either melee, ranged, abilities, or magic.\n- `multiple`\
  \ - When this option is chosen, all of its child options are chosen, and must be\
  \ resolved the same way as a normal option.\n  - `items` (array): An array of Option\
  \ objects. All of them must be taken if the option is chosen.\n- `choice` - A nested\
  \ choice. If this option is chosen, the Choice structure contained within must be\
  \ resolved like a normal Choice structure, and the results are the chosen options.\n\
  \  - `choice` (Choice): The Choice to resolve.\n- `string` - A terminal option.\
  \ Contains a reference to a string.\n  - `string` (string): The string.\n- `ideal`\
  \ - A terminal option. Contains information about an ideal.\n  - `desc` (string):\
  \ A description of the ideal.\n  - `alignments` (ApiReference[]): A list of alignments\
  \ of those who might follow the ideal.\n- `counted_reference` - A terminal option.\
  \ Contains a reference to something else in the API along with a count.\n  - `count`\
  \ (number): Count.\n  - `of` (ApiReference): Thing being referenced.\n- `score_prerequisite`\
  \ - A terminal option. Contains a reference to an ability score and a minimum score.\n\
  \  - `ability_score` (ApiReference): Ability score being referenced.\n  - `minimum_score`\
  \ (number): The minimum score required to satisfy the prerequisite.\n- `ability_bonus`\
  \ - A terminal option. Contains a reference to an ability score and a bonus\n  -\
  \ `ability_score` (ApiReference): Ability score being referenced\n  - `bonus` (number):\
  \ The bonus being applied to the ability score\n- `breath` - A terminal option:\
  \ Contains a reference to information about a breath attack.\n  - `name` (string):\
  \ Name of the breath.\n  - `dc` (DC): Difficulty check of the breath attack.\n \
  \ - `damage` ([Damage]): Damage dealt by the breath attack, if any.\n- `damage`\
  \ - A terminal option. Contains information about damage.\n  - `damage_type` (ApiReference):\
  \ Reference to type of damage.\n  - `damage_dice` (string): Damage expressed in\
  \ dice (e.g. \"13d6\").\n  - `notes` (string): Information regarding the damage.\n\
  \n## FAQ\n\n### What is the SRD?\nThe SRD, or Systems Reference Document, contains\
  \ guidelines for publishing content under the OGL. This allows for some of the data\
  \ for D&D 5e to be open source. The API only covers data that can be found in the\
  \ SRD. [Here's a link to the full text of the SRD.](https://media.wizards.com/2016/downloads/DND/SRD-OGL_V5.1.pdf)\n\
  \n### What is the OGL?\nThe Open Game License (OGL) is a public copyright license\
  \ by Wizards of the Coast that may be used by tabletop role-playing game developers\
  \ to grant permission to modify, copy, and redistribute some of the content designed\
  \ for their games, notably game mechanics. However, they must share-alike copies\
  \ and derivative works. [More information about the OGL can be found here.](https://en.wikipedia.org/wiki/Open_Game_License)\n\
  \n### A monster, spell, subclass, etc. is missing from the API / Database. Can I\
  \ add it?\nPlease check if the data is within the SRD. If it is, feel free to open\
  \ an issue or PR to add it yourself. Otherwise, due to legal reasons, we cannot\
  \ add it.\n\n### Can this API be self hosted?\nYes it can! You can also host the\
  \ data yourself if you don't want to use the API at all. You can also make changes\
  \ and add extra data if you like. However, it is up to you to merge in new changes\
  \ to the data and API.\n\n#### Can I publish is on <insert platform>? Is this free\
  \ use?\nYes, you can. The API itself is under the [MIT license](https://opensource.org/licenses/MIT),\
  \ and the underlying data accessible via the API is supported under the SRD and\
  \ OGL.\n\n# Status Page\n\nThe status page for the API can be found here: https://5e-bits.github.io/dnd-uptime/\n\
  \n# Chat\n\nCome hang out with us [on Discord](https://discord.gg/TQuYTv7)!\n\n\
  # Contribute\n\nThis API is built from two repositories.\n  - The repo containing\
  \ the data lives here: https://github.com/bagelbits/5e-database\n  - The repo with\
  \ the API implementation lives here: https://github.com/bagelbits/5e-srd-api\n\n\
  This is a evolving API and having fresh ideas are always welcome! You can\nopen\
  \ an issue in either repo, open a PR for changes, or just discuss with\nother users\
  \ in this discord.\n"
logo: "dnd5eapi.co-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "open_data"
stubs: "dnd5eapi.co-stubs.json"
swagger: "dnd5eapi.co-swagger.json"
---
