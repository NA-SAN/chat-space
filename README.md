# DB設計

## users table

|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false, unique: true|
|password|integer|null: false|
|mail|string|null: false, unique: true|


### Association
- has_many :messages
- has_many :users_groups
- has_many :groups, thought: :users_groups


## groups table

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :messages
- has_many :users_groups
- has_many :users, thought: :users_groups


## users_goups

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group


## messages table

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|
|body|text|
|image|string|


### Association
- belongs_to :user
- belongs_to :group
