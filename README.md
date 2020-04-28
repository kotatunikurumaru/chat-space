## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|index: true,null: false, unique: true|
|mail|string|null: false, unique: true|

### Association
- has_many :groups,through: members
- has_many :messages
- has_many :members

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false, unique: true|

### Association
- has_many :groups_users
- has_many :users, through: groups_users
- has_many :messages

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user