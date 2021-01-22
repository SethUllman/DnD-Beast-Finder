# README

Rails Backend for Guidance, a DnD 5e app for Druids.

# MVP
- Users can create a character by level and circle chosen at lvl 3
- Users can update characters level
- Users can search available spells and add to prepared list
- Users can update spell slots and wildshapes used
- Users can search Beasts by Challenge Rating
- Users can get random Beast by Challenge Rating
- Users can add beasts to WildShapes Known
- Users can view Beast DataSheets

# Models
### Users
```
  has_many :characters
  foreign_key: :character_id
  class: :Character
```

### Character
```
  belongs_to :user
  foreign_key: :user_id
  class: :User

  has_many :spells_known
  foreign_key: :spells_known_id
  class: :Spells_Known

  has_many :spells
  through: :spells_known
  source: :Spells
  
  has_many :wildshapes
  foreign_key: :wildshapes_id
  class: :Wildshapes

  has_many :beasts
  through: :wildshapes
  source: :Beasts
```
### SpellsKnown
```
  belongs_to :character
  foreign_key: :character_id
  class: :Character

  belongs_to :spells
  foreign_key: :spell_id
  class: :Spells
```
### Wildshapes
```
  belongs_to :character
  foreign_key: :character_id
  class: :Character

  belongs_to :beasts
  foreign_key: :beast_id
  class: :Beast
```
### Spells
```
  has_many :spells_know
  foreign_key: :spells_known_id
  class: :SpellsKnown
```
### Beasts
```
  has_many :wildshapes
  foreign_key: :wildshape_id
  class: :Wildshapei
```