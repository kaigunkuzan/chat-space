# chat space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|nickname|string|null: false,index: true|
### Association
- has_many :tweets
- has_many :groups, through:  :groups_users
- has_many :groups_users
## tweetsテーブル
|Column|Type|Options|
|------|----|-------|
|image|text||
|text|text||
|user|references|null: false,foreign_key: true|
|group|references|null: false,foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :tweets
- has_many :users, through:  :groups_users
- has_many :groups_users
## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|refereces|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user