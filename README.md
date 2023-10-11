# Platform for Job Hunting

Logvinov Andrey 153501

## Functional requirements

### 1. Authorized User Flow:
- Users can register with an email (/^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/), username, first name, and last name.
- Users can log in using their registered email.
- Users can view and update their personal details (firstName, lastName, email, username).
- Users can choose role - organisator, admin, visiter  
- Organisator can add new BeerEvent or create a new brewery 
- Organisator can add new sort of beer or collection
- Organisator can add new pair of food 
- Admin can manage all information, which was added by organisator
- All users can select event and set a rating for beer

### 2. Unauthorized User Flow:
- Users can view a list of BeerEvents, Breweries, Collections, Beer and all info about beer

### 3. Orgainisator Flow:
- Organisator can register with an email, company name, and other essential details.
- Organisator can log in using their registered email.
- Organisator can create and manage their events, which includes associating with an collections and beer types
- Organisator can view, edit, or delete their events.
- Organisator can invite users to event
- Organisator can CRUD all type of own beers
- Organisator can give responses for users comments

### 4. Admin Flow:
- Admins can manage the list of BeerEvents, adding, editing, or deleting their parts.
- Admins can view, edit, or delete any organisator profile.
- Admins can view, edit, or delete any user profile.
- Admins can manage all type of beers in system
- Admins can manage user reviews and comments, including approving, editing, or deleting them.

## Models restrictions

(OTM O_Breewery, M_Beer)
(OTM O_BeerType, M_Beer)
(OTM O_Beer, M_FoodPairing)
(OTM O_Beer, M_BeerRating)
(OTM O_Collection, M_Beer)
Beer:
+ Name: String
+ Description: String
+ Photo: String(path)
+ Id: Int

(OTM O_BeerType, M_Beer)
(OTM O_Color, M_BeerType)
(OTM O_Strength, M_BeerType)
BeerType:
+ Category: String
+ Id: Int

(OTM O_Color, M_BeerType)
Color:
+ Name: String
+ Id: Int

(OTM O_Strength, M_BeerType)
Strength:
+ Name: String
+ Id: Int


(OTM O_User, Brewery)
(OTM O_Brewery, Beer)
Brewery:
+ Name: String
+ PhoneNumber: String
+ Location: String
+ Region: String
+ Id: Int

(OTM O_User, Breewery)
(OTM O_Role, User)
(OTM O_User, BeerEvent)(participates)
(OTM O_User, BeerEvent)(organizes)
(OTM O_User, Collections)
(OTM O_User, BeerRating)
User:
+ Username: String
+ Email: String
+ Password: String
+ ProfilePicture: Data
+ FirstName: String
+ LastName: String
+ Id: Int

(OTM O_Role, User)
Role:
+ Name: String
+ Id: Int

(OTM O_Beer, BeerRating)
(OTM O_User, BeerRating)
BeerRating:
+ Rating: Int
+ Description: String(optional)
+ Id: Int

(OTM O_User,Collection)
(MTM Beer, Collection)
Collection:
+ Name: String
+ Description: String
+ Id: Int

(MTM Food, FoodPairings)
(OTM O_Beer, M_FoodPairings)
FoodPairings:
+ Description: String
+ Id: Int

(MTM FoodPairings, Food)
Food
+ Name: String
+ Description: String
+ Photo: String(path)
+ Id: Int

(MTM User)(organised by)
(MTM User)(accepts them)
(MTM Beer)
Beer Events:
+ Name: String
+ Date: String
+ Location: String
+ Id: Int
