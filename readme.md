# Profile and Sync Services

Profile and Sync services are part of the OneGuest project effort and they are intended to attend the following actions:

- #### [Get Profiles by Gaming Id](#get-profile-by-gaming-id)
- #### [Create/Update Profile](#create---update-profile)

# Profile Service
## Get Profile by Gaming Id
### Description
Fetches the profile information related to the gaming id sent on the URL
#### Resource address

    GET: /profiles/{gamingId}

#### Parameters

 - gamingId `STRING` `REQUIRED` : GamingId of profile to return

#### Responses

##### Model

|Name| Type| Sample value | Required
|--|--|--|--|
| profileId | string  | 123e4567-e89b-12d3-a456-426655440000 | X 
|firstName|string |Ricardo| X
| middleName | string | D | 
|lastName|string|Martinez|X
|gamingId|string|333434122211|
|DOB|string|01/01/2020|
|addresses|**[{address1** `string`  `required`  _**address2**_  `string`  _**city**_  `string`  `required`  _**stateProvince**_  `string`  _**postalCode**_  `string`  _**country**_  `string`  _**addressType**_  `(home, vacationHome, other)`**}]**|{"address1": "5701 Sterling Dr", "address2": "2nd floor", "city":"Davie", "stateProvince":"FL","postalCode":"94595","country":"USA","addressType":"vacationHome"}]
|communication|**{primaryEmail** `string` **alternateEmail** `string` **homePhone** `string` **workPhone** `string` **cellPhone** `string` `required`**}**|{"primaryEmail":"r@shrss.com","alternateEmail":"s@shrss.com","homePhone":"000-000-0000","workPhone":"000-000-0000","cellPhone":"000-000-0000"}|

##### Results set
|Code| Description  | Sample value |
|--|--|--|
| 200 | successful operation  | `{  "profileId":  "123e4567-e89b-12d3-a456-426655440000",  "firstName":  "Ricardo",  "middleName":  "X",  "lastName":  "Martinez",  "gamingId":  "333434122211",  "DOB":  "01/01/2020",  "addresses":  [  {  "address1":  "string",  "address2":  "x",  "city":  "Davie",  "stateProvince":  "FL",  "postalCode":  94595,  "country":  "USA",  "addressType":  "home"  }  ],  "communication":  {  "primaryEmail":  "r@shrss.com",  "alternateEmail":  "r@shrss.com",  "homePhone":  "000-000-0000",  "workPhone":  "000-000-0000",  "cellPhone":  "000-000-0000"  }  }` 
|400|invalid ID supplied||
|404|profile not found||

# Sync Service
## Create - Update Profile
### Description
If exists, updates the profile information related to the gaming ID sent on the request body. Otherwise, it creates a new one using that information.
#### Resource address

    PUT: /sync

#### Request Body

|Name| Type| Sample value | Required|
|--|--|--|--|
|firstName|string |Ricardo| X|
| middleName | string | D | 
|lastName|string|Martinez|X
|gamingId|string|333434122211|
|DOB|string|01/01/2020|
|addresses|**[{address1** `string`  `required`  _**address2**_  `string`  _**city**_  `string`  `required`  _**stateProvince**_  `string`  _**postalCode**_  `string`  _**country**_  `string`  _**addressType**_  `(home, vacationHome, other)`**}]**|{"address1": "5701 Sterling Dr", "address2": "2nd floor", "city":"Davie", "stateProvince":"FL","postalCode":"94595","country":"USA","addressType":"vacationHome"}]
|communication|**{primaryEmail** `string` **alternateEmail** `string` **homePhone** `string` **workPhone** `string` **cellPhone** `string` `required`**}**|{"primaryEmail":"r@shrss.com","alternateEmail":"s@shrss.com","homePhone":"000-000-0000","workPhone":"000-000-0000","cellPhone":"000-000-0000"}|

#### Responses
##### Model
|Name| Type| Sample value | Required|
|--|--|--|--|
| profileId | string  | 123e4567-e89b-12d3-a456-426655440000 | X |
|primaryDetailsUpdated|boolean|true||

##### Results set
|Code| Description  |Sample Value
|--|--|--|
|200|successful operation|{  "profileId":  "123e4567-e89b-12d3-a456-426655440000",  "primaryDetailsUpdated":  true  }|
|405|Invalid input||
