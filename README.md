# README
# DB設計

  ## users table
  |Column|Type|Options|
  |------|----|-------|
  |name|string|index:true, null: false, unique: true|
  |email|string|null: false, unique: true|
  |password|string|null: false|

  ### Association
  - has_many :groups, through: :members
  - has_many messages

  ## groups table
  |column|Type|Options|
  |------|----|-------|
  |name|string|index:true, null: false|
  |user_id|integer|null: false, foreign_key: true|

  ### Association
  - has_many :users, through: :members
  - has_many :messages

  ## members table
  |column|Type|Options|
  |------|----|-------|
  |user_id|integer|null: false, foreign_key: true|
  |group_id|integer|null: false, foreign_key: true|

  ### Association
  - belongs_to :user
  - belongs_to :group

  ## messages table
  |Column|Type|Options|
  |------|----|-------|
  |body|text|null: false|
  |image|string||
  |user_id|integer|foreign_key: true|
  |group_id|integer|foreign_key: true|

  ### Association
  - belongs_to :user
  - belongs_to :group

