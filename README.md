# 🤖 lowline.ai

[🔗 Website](https://www.lowline.ai)
[🔗 Documentation](https://www.lowline.ai/getting-started)

Lowline.ai is a javascript utility library that lets you easily sprinkle powerful AI magic all through your codebases.

- 100+ functions powered by ChatGPT, with more added all the time.
- Use it straight away by installing the NPM module.
- For faster completions sign up for a pay-per-use plan and create an API key.

---

## 🚧 Under development 🚧

---

## 📖 Table of Contents

- [Getting started](#-getting-started)
- [Full list of functions](#-full-list-of-functions)
- [Pricing](#-pricing)

---

## 🚀 Getting started

Install the NPM package

```bash
npm install lowline.ai
```

Once the package is installed you can import using the require or import approach.

```js
// import
import { _ai } from "lowline.ai";

// or require
const lowline = require("lowline.ai");
const _ai = lowline._ai;
```

Search example

```js
import { _ai } from "lowline.ai";

const list = ["test1", "test2", "test3", "test4", "test5"],

const res = await _ai.searchStringList({
  count: 1,
  search_term: "second test",
  search_items: list,
});
if (res.error) {
  console.log(error)
} else {
  console.log(res.data) // --> ["test2"]
}
```

Recommendation example

```js
import { _ai } from "lowline.ai";

const purchases = ["apple", "banana"];
const products = [
  "apple",
  "banana",
  "orange",
  "grape",
  "eggs",
  "chicken",
  "potato",
  "pasta",
];

const res = await _ai.recommendStringList({
  options: products,
  interests: purchases,
  count: 3,
});
if (res.error) {
  console.lg(rec.error);
} else {
  console.log(rec.result); // -->  ["orange", "grape", "pasta"]
}
```

---

# 📒 Full list of functions

---

## 🔍 Search and recommend

### option_list

```php
{ id: string; text: string; }[];

```


#### _ai.searchOptionList

Search for one or more options from a list of options, based on a search term.

```js
const search_term = "Best place to go for a nature walk and hear the ocean";
const options = [
  { id: "967ea024-b996-11ed-afa1-0242ac120002", text: "The beach" },
  {
    id: "a9c50ee8-b996-11ed-afa1-0242ac120002",
    text: "The local mall",
  },
  {
    id: "c4b2d762-b996-11ed-afa1-0242ac120002",
    text: "A botanical garden",
  },
  {
    id: "d5956108-b996-11ed-afa1-0242ac120002",
    text: "On a treadmill at the gym",
  },
  {
    id: "f129c558-b996-11ed-afa1-0242ac120002",
    text: "Down the main street of your town",
  },
];

const res = await _ai.searchOptionList({
  count: 1,
  search_term,
  options,
});
if (res.error) {
  console.log(res.error);
} else {
  console.log(res.result); // --> The beach
}
```


#### _ai.recommendOptionList

Recommend one or more options from a list of options, based on a list of interests.

```js
const res = await _ai.recommendOptionList({
  count: 2,
  interests: [
    {
      id: "53932a26-b9a2-11ed-afa1-0242ac120002",
      text: "Clothes shopping",
    },
    {
      id: "69dc9b78-b9a2-11ed-afa1-0242ac120002",
      text: "History",
    },
  ],
  options: [
    { id: "967ea024-b996-11ed-afa1-0242ac120002", text: "The beach" },
    {
      id: "a9c50ee8-b996-11ed-afa1-0242ac120002",
      text: "The local mall",
    },
    {
      id: "c4b2d762-b996-11ed-afa1-0242ac120002",
      text: "A forest reserve",
    },
    {
      id: "d5956108-b996-11ed-afa1-0242ac120002",
      text: "The sports club",
    },
    {
      id: "f129c558-b996-11ed-afa1-0242ac120002",
      text: "The local heritage museum",
    },
  ],
});
if (res.error) {
  console.log(res.error);
} else {
  console.log(res.result);
  // [
  //   {
  //     id: "a9c50ee8-b996-11ed-afa1-0242ac120002",
  //     text: "The local mall",
  //   },
  //   {
  //     id: "f129c558-b996-11ed-afa1-0242ac120002",
  //     text: "The local heritage museum",
  //   },
  // ],
}
```


#### _ai.createOptionList

Create a list of options, based on a option type that describes the kind of options to create.

```js
const res = await _ai.createOptionList({
  count: 3,
  option_type: "largest countries by land area, descending",
});
if (res.error) {
  console.log(res.error);
} else {
  console.log(res.result);
  // [
  //   {
  //     id: "42b58fce-b9b5-11ed-afa1-0242ac120002",
  //     text: "Russia",
  //   },
  //   {
  //     id: "4b3dd782-b9b5-11ed-afa1-0242ac120002",
  //     text: "Canada",
  //   },
  //   {
  //     id: "5310e8aa-b9b5-11ed-afa1-0242ac120002",
  //     text: "China",
  //   },
  // ],
}
```


#### _ai.sortOptionList

Sort a list of options, based on a criteria.

```js
const res = await _ai.sortOptionList({
  criteria: "Hardness",
  options: [
    {
      id: "8a715e2c-b9a8-11ed-afa1-0242ac120002",
      text: "Granite",
    },
    {
      id: "a4b270fa-b9a8-11ed-afa1-0242ac120002",
      text: "Polystyrene foam",
    },
    {
      id: "800c6e9a-b9a8-11ed-afa1-0242ac120002",
      text: "Diamond",
    },
    {
      id: "9730bc02-b9a8-11ed-afa1-0242ac120002",
      text: "Wood",
    },
  ],
});
if (res.error) {
  console.log(res.error);
} else {
  console.log(res.result);
  // [
  //   {
  //     id: "800c6e9a-b9a8-11ed-afa1-0242ac120002",
  //     text: "Diamond",
  //   },
  //   {
  //     id: "8a715e2c-b9a8-11ed-afa1-0242ac120002",
  //     text: "Granite",
  //   },
  //   {
  //     id: "9730bc02-b9a8-11ed-afa1-0242ac120002",
  //     text: "Wood",
  //   },
  //   {
  //     id: "a4b270fa-b9a8-11ed-afa1-0242ac120002",
  //     text: "Polystyrene foam",
  //   },
  // ]
}
```


#### _ai.filterOptionList

Filter a list of options, based on a criteria.

```js
const res = await _ai.filterOptionList({
  criteria: "Types of rocks",
  options: [
    {
      id: "8a715e2c-b9a8-11ed-afa1-0242ac120002",
      text: "Granite",
    },
    {
      id: "a4b270fa-b9a8-11ed-afa1-0242ac120002",
      text: "Polystyrene foam",
    },
    {
      id: "800c6e9a-b9a8-11ed-afa1-0242ac120002",
      text: "Sandstone",
    },
    {
      id: "9730bc02-b9a8-11ed-afa1-0242ac120002",
      text: "Wood",
    },
  ],
});
if (res.error) {
  console.log(res.error);
} else {
  console.log(res.result);
  // [
  //   {
  //     id: "8a715e2c-b9a8-11ed-afa1-0242ac120002",
  //     text: "Granite",
  //   },
  //   {
  //     id: "800c6e9a-b9a8-11ed-afa1-0242ac120002",
  //     text: "Sandstone",
  //   },
  // ],
}
```

### `string_list`

- searchStringList
- recommendStringList
- createStringList
- sortStringList
- filterStringList

## 💬 Messaging

### `chat_message`

- suggestChatResponse
- suggestChatResponseIntents
- suggestChatResponseMultiple

### `chat_chain`

- suggestChatChainResponse
- suggestChatChainResponseIntents
- suggestChatChainResponseMultiple

### `email_message`

- suggestEmailResponse
- suggestEmailResponseIntents
- suggestEmailResponseMultiple

### `email_chain`

- suggestEmailChainResponse
- suggestEmailChainResponseIntents
- suggestEmailChainResponseMultiple

## 📘 Text processing

### `plaintext`

- hasSpellingMistakes
- fixSpelling
- hasGrammarMistakes
- fixGrammar
- hasProfanity
- getProfanityValue
- removeProfanity
- getReasonableness
- includesMentionOf
- isQuestion
- proofread // suggest edits to improve readability
- summarize
- elaborate
- explain
- pluralize
- convertToMarkdown
- convertToHTML

### `emoji`

- detectEmoji
- suggestEmoji

### `formality`

- detectFormality
- detectFormalityValue
- editFormality

### `sentiment`

- detectMainSentiment
- getSentimentHappiness
- getSentimentAnger
- getSentimentSadness
- getSentimentDisgust
- getSentimentFear
- getSentimentSurprise
- changeSentiment

### `html`

- hasHTML
- removeHTML
- convertHTMLToMarkdown
- convertHTMLToPlainText

### `markdown`

- hasMarkdown
- removeMarkdown
- convertMarkdownToHTML
- convertMarkdownToPlainText

## 🌍 Geography

### `coordinates`

- convertCoordsToAddress
- getDistanceBetweenCoords
- getCoordsFromAddress
- getCoordsFromLocation

### `location`

Open-ended, city, state, country, etc.

- detectLocation
- suggestLocation
- suggestLocationMultiple
- getCoordsFromLocation
- getAddressFromLocation
- getTimezoneFromLocation
- getCurrencyFromLocation
- getLanguageFromLocation
- getCountryFromLocation
- getStateFromLocation
- getCityFromLocation

### `country`

- detectCountry
- suggestCountry
- suggestCountryMultiple
- getCurrencyFromCountry
- getCountryCode
- getCountryName
- getCountryFlagEmoji

### `currency`

- getCurrencySymbol
- getCurrencyCode
- getCurrencyName

### `timezone`

- detectTimezone
- getTimezoneName
- getTimezoneOffset
- getTimezoneAbbreviation
- getTimezoneUTCOffset

### `language`

- detectLanguage
- getLanguageCode
- getLanguageName
- translate

## 🧮 Number representation

### `color`

- isColor
- getColorName
- getColorFormat
- convertColorFormat
- suggestColor
- suggestColorMultiple
- getBrightness
- getSaturation
- getHue
- setBrightness
- setSaturation
- setHue
- getComplementaryColor
- invertColor
- getContrastingColor

### `url`

- isURL
- getURLProtocol
- getURLDomain
- getURLSubdomain
- getURLPathname
- getURLQueryParams

### `decimal`

- toDecimal
- fromDecimal

### `percentage`

- prettyPrintPercentage
- ratioToPercentage // 0-1 to 0-100
- percentageToRatio // 0-100 to 0-1

### `fraction`

- prettyPrintFraction
- ratioToFraction // 0-1 to fraction
- fractionToRatio // fraction to 0-1

### `number`

- isNumber
- isWholeNumber
- isDecimal
- isPercentage
- isFraction
- isNegative
- isPositive

## 📍 Addresses and contact info

### `names`

- detectName
- suggestName
- suggestNameMultiple
- getFirstName
- getLastName
- getFullName
- getInitials

### `address`

- detectAddress
- suggestAddress
- formatAddress
- getStreetAddress
- getCityFromAddress
- getStateFromAddress
- getZipCodeFromAddress
- getCountryFromAddress

### `email_address`

- isEmailAddress

### `phone_number`

- isPhoneNumber
- getPhoneNumberCountryCode
- getPhoneNumberAreaCode
- getPhoneNumberLocalNumber
- getPhoneNumberExtension
- getPhoneNumberType

## 💽 Data formats

### `json`

- isJSON
- flattenJSON
- convertJSONToYAML
- convertJSONToXML
- convertJSONToCSV

### `xml`

- isXML
- convertXMLToJSON
- convertXMLToYAML
- convertXMLToCSV

### `yaml`

- isYAML
- convertYAMLToJSON
- convertYAMLToXML
- convertYAMLToCSV

### `csv`

- isCSV
- convertCSVToJSON
- convertCSVToXML
- convertCSVToYAML

---

## 🏷️ Pricing

The free version has a small delay, for faster completions, go to https://www.lowline.ai, sign up for a paid account and create an API Key.

- Unlimited free use with a small delay.
- This delay is currently 5 seconds
- For no delay, create a paid plan at USD $0.01 per request.
- Pricing and delay length may change if needed to make the project financially sustainable.

Stay tuned!
