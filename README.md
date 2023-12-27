# Platform for WineEvent

Logvinov Andrey 153501

## Functional requirements
User roles:

•	simple customer
CRUD its collections, wine ratings,

•	Sommelier
 Simple customer + CRUD food & food pairings

•	Winery Owner
Simple customer + CRUD its winery

•	Organizer
Simple customer + CRUD its wine events

•	Admin
CRUD everything


User authorization.
Logging of user actions.


(OTM O_Winery, M_Wines)
(OTM O_Vintage, M_Wines)
(OTM O_WineType, M_Wines)
(OTM O_Wine, M_FoodPairing)
(OTM O_Wine, M_WineRating)
(OTM O_Collection, M_Wine)
(MTM WineEvent)
Wines:
+ Name: varchar
+ Description: varchar
+ Photo: varchar

(OTM O_Vintage, Wines)
Vintage:
+ Year: number(4)

(OTM O_WineType, M_Wines)
(OTM O_Color, WineType)
(OTM O_Sweetness, WineType)
WineType:
+ Sparkling: bool

(OTM O_Color, WineType)
Color:
+ Name: varchar
+ Id: number(for enum)

(OTM O_Sweetness, WineType)
Sweetness:
+ Name: varchar
+ Id: number(for enum)


(OTM O_User, Wineries)
(OTM O_Winery, Wines)
Winery:
+ Name: varchar
+ PhoneNumber: varchar
+ Location: varchar
+ Region: varchar

(OTM O_User, Winary)
(OTM O_Role, User)
(OTM O_User, WineEvent)(participates)
(OTM O_User, WineEvent)(organizes)
(OTM O_User,Collections)
(OTM O_User, WineRating)
User:
+ Username: varchar
+ Email: varchar
+ Password: varchar
+ ProfilePicture: varchar(path to photo)
+ FirstName: varchar
+ LastName: varchar

(OTM O_Role, User)
Role:
+ Name: varchar
+ Id: number(*)


(OTM O_Wine, WineRating)
(OTM O_User, WineRating)
WineRating:
+ Rating: number(2)
+ Description: varchar(optional)

(OTM O_User,Collection)
(MTM Wine)
Collection:
+ Name: varchar
+ Description: varchar

(MTM Food)
(OTM O_Wine, M_FoodPairings)
FoodPairings:
+ Description: varchar

(MTM FoodPairings)
Food
+ Name: varchar
+ Description: varchar
+ Photo: varchar

(MTM User)(organised by)
(MTM User)(accepts them)
(MTM Wine)
Wine Events:
+ Name: varchar
+ Date: date
+ Location: varchar

