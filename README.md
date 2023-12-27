# Platform for WineEvent

Logvinov Andrey 153501

## Functional requirements
### 1. Authorized User Flow:
- **User Registration:**
  - Users can register with a valid email, username, first name, and last name.
  - Password validation follows the pattern /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/.
- **User Login:**
  - Users can log in using their registered email.
- **User Profile Management:**
  - Users can view and update their personal details (firstName, lastName, email, username).
  - Users can choose a role: Organisator, Admin, or Visitor.
- **Organisator Actions:**
  - Organisators can add new BeerEvents or create a new brewery.
  - Organisators can add new types of beer or collections.
  - Organisators can add new food pairings.
  - Organisators can manage and invite users to events.
  - Organisators can CRUD all types of their own beers.
  - Organisators can respond to user comments.

- **Beer Rating:**
  - All users can select events and rate beers.

### 2. Unauthorized User Flow:
- **View-Only Access:**
  - Users can view a list of BeerEvents, Breweries, Collections, Beers, and related information.

### 3. Organisator Flow:
- **Organisator Registration:**
  - Organisators can register with an email, company name, and other essential details.
- **Organisator Login:**
  - Organisators can log in using their registered email.
- **Event Management:**
  - Organisators can create and manage events, associating them with collections and beer types.
  - Organisators can view, edit, or delete their events.
  - Organisators can invite users to events.
- **Beer Management:**
  - Organisators can CRUD all types of their own beers.
  - Organisators can respond to user comments.

### 4. Admin Flow:
- **BeerEvent Management:**
  - Admins can manage the list of BeerEvents, adding, editing, or deleting their parts.
- **Organisator Profile Management:**
  - Admins can view, edit, or delete any organisator profile.
- **User Profile Management:**
  - Admins can view, edit, or delete any user profile.
- **Beer Management:**
  - Admins can manage all types of beers in the system.
- **Review and Comment Management:**
  - Admins can manage user reviews and comments, including approving, editing, or deleting them.

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

