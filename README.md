Simple wrapper around js-vat from John Gardner (http://www.braemoor.co.uk/software/vat.shtml)

Added a function to check if a country can use a given VAT number (useful for forms):

### function checkVATNumber (myVATNumber, countryCode)

This function checks the value of the parameter for a valid European VAT number and a given country code.

Parameters:    
  - myVATNumber: VAT number be checked.
  - countryCode: (optional) two letters country code, to be matched against the VAt number.

Return:
  - number: the re-formatted VAT number.
  - valid_vat: if the number is valid in itself.
  - valid_country: if the country of the VAT number matches the optional countryCode param.
  
Usage:
```javascript
  
  var checkVATObject = checkVATNumber(myVATNumber, countryCode);
  
  if (checkVATObject.valid_country) 
      alert ("VAT Number does match the country code")
  else 
      alert ("VAT number doesn't match the country code");

  if (checkVATObject.valid_vat) 
      alert ("VAT number has a valid format")
  else 
      alert ("VAT number has invalid format");
                    
```

### Examples

```javascript
checkVATNumber("FR 37 50 999 58 09")
Object {valid_country: true, valid_vat: true, number: "FR37509995809"}

checkVATNumber("FR 37 50 999 58 09", "FR")
Object {valid_country: true, valid_vat: true, number: "FR37509995809"}

checkVATNumber("FR 37 50 999 58 09", "XX")
Object {valid_country: false, valid_vat: true, number: "FR37509995809"}

checkVATNumber("XX 37 50 999 58 09", "XX")
Object {valid_country: false, valid_vat: false, number: "XX37509995809"}

checkVATNumber("XX 37 50 999 58 09", "FR")
Object {valid_country: true, valid_vat: false, number: "XX37509995809"}

```

```
Version:       V1.0
Date:          30th July 2005
Description:   Used to check the validity of an EU country VAT number

Version:       V1.1
Date:          3rd August 2005
Description:   Lithunian legal entities & Maltese check digit checks added.

Version:       V1.2
Date:          20th October 2005
Description:   Italian checks refined (thanks Matteo Mike Peluso).

Version:       V1.3
Date:          16th November 2005
Description:   Error in GB numbers ending in 00 fixed (thanks Guy Dawson).

Version:       V1.4
Date:          28th September 2006
Description:   EU-type numbers added.

Version:       V1.5
Date:          1st January 2007
Description:   Romanian and Bulgarian numbers added.

Version:       V1.6
Date:          7th January 2007
Description:   Error with Slovenian numbers (thanks to Ales Hotko).

Version:       V1.7
Date:          10th February 2007
Description:   Romanian check digits added. Thanks to Dragu Costel for test suite.

Version:       V1.8
Date:          3rd August 2007
Description:   IE code modified to allow + and * in old format numbers. Thanks to Antonin Moy of 
               Spehere Solutions for pointing out the error.

Version:       V1.9
Date:          6th August 2007
Description:   BE code modified to make a specific check that the leading character of 10 digit 
               numbers is 0 (belts and braces).

Version:       V1.10
Date:          10th August 2007
Description:   Cypriot check digit support added.
               Check digit validation support for non-standard UK numbers

Version:       V1.11
Date:          25th September 2007
Description:   Spain check digit support for personal numbers.
               Author: David Perez Carmona

Version:       V1.12
Date:          23rd November 2009
Description:   GB code modified to take into account new style check digits.
               Thanks to Guy Dawson of Crossflight Ltd for pointing out the necessity.

Version:       V1.13
Date:          7th July 2012
Description:   EL, GB, SE and BE formats updated - thanks to Joost Van Biervliet

Version:       V.14
Date:          8th April 2013
Description:   BE Pattern match refined
               BG Add check digit checks for all four types of VAT number
               CY Pattern match improved
               CZ Personal pattern match checking improved
               CZ Personal check digits incorporated
               EE improved pattern match
               ES Physical person number checking refined
               GB Check digit support provided for 12 digit VAT codes and range checks included
               IT Bug removed to allow 999 and 888 issuing office codes
               LT temporarily registered taxpayers check digit support added
               LV Natural persons checks added
               RO improved pattern match
               SK improved pattern match and added check digit support
               
               Thanks to Theo Vroom for his help in this latest release.
               
Version:      V1.15
Date:         15th April 2013
              Swedish algorithm re-implemented.
               
Version:      V1.16
Date:         25th July 2013
              Support for Croatian numbers added

```
