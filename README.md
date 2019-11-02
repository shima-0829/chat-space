## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|tetx|null: false|
|image|string|null: false|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group


## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user


## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :messages
- has_many :users, through: :groups_users


## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|text|null: false|
|password|text|null: false|

### Association
- has_many :messages
- has_many :groups, through: :groups_users