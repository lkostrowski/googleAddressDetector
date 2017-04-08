# Google geocode address detector

## FEATURES
 - Get formatted addresses and address parts
 - Uses promises
 - Has predefined presets for most common "smart validation" uses
 
## Dependencies:
 jQuery 3+ or axios  
 
## Roadmap:
- [ ] Add dependency injection of ajax service
- [ ] Switch to google autocomplete api - optional (better place predictions)
- [ ] Add unit tests :D
- [ ] Add build to the repo 
 
## API
### Start:
```javascript
import GoogleDetector from './GoogleDetectorAxios';

const detector = new GoogleDetector( options );

```

### Options: 

```
let options = {
    language: String,
    region: String,
    apiKey: String,
    dev: Boolean
}
```
Where `language` and `region` are ISO codes for countries (language of results and region where results will be filtered by),
fe: `DE`

`apiKey` is google key, needed for production (only https AFAIK), no need in dev

`dev` logs errors with api

### Methods: 
`getResults(query)` gets raw results from google api based on query
 
`getFormatedResults(query)` gets formatted results in `{formattedResult}` object (see below)

`getFormattedAddres(rawResult)` gets formatted addres based on single raw result from api

`getCityByPostalCode(postalCode)` gets city name from postal code provided

`getPostalCodeByFullStreet` gets postal code by street + street number string (first matched)

`getCorectStreetName` gets street name based on street name - if google has corrected it, else - null

### formattedResult object
It's object returned by `getFromattedResults` and `getFormattedAddress` methods.

Format is:
```javascript
{
    full: String,
    street: String,
    city: String,
    streetNumber: String,
    postalCode: String
}
```

Where `full` is formatted, full address ('Zabłocie 25, 30-701 Kraków Polska),
and rest of keys are strings with address parts, if any. Alse, the key doesn't exist
