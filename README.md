#　DB設計

## users Table

|Column|Type|Option|
|------|----|------|
|name|string|index: true, null: false, unique: true|
|mail|string|null: false, unique: true|
|password|string|null: false|

### Association

- has_many :groups, through: :members
- has_many :messages

## members Table

|Column|Type|Option|
|------|----|------|
|group_id|integer|unique: true, foreign_key: true|
|user_id|integer|unique: true, foreign_key: true|

### Association

- belongs_to :user
- belongs_to :group

## groups Table

|Column|Type|Option|
|------|----|------|
|name|string|index: true, null: false, unique: true|

### Association

- has_many :users, through: :members
- has_many :messages

## messages Table

|Column|Type|Option|
|------|----|------|
|message|text||
|update|date|null: false|

### Association

- belongs_to :users
- belongs_to :groups
