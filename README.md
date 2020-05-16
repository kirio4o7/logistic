# 概要
logistic system
内職指示書の簡易管理システムにチャット機能を追加で付けてます。

# デモURL

# バージョン
・Ruby 2.5.1
・Rails 5.0.7.2

# logistic systemのDB設計

# usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null:false, index: true|
|password|string|null:false, unique: true|
|username|string|null: false|
# Association
- has_many :groups_users
- has_many :mesasages
- has_many :groups, through: :groups_users
- belongs_to :directed

# directedテーブル
|Column|Type|Options|
|------|----|-------|
|text|text||
|data|mediumblob||
|create_id|reference|null: false|
|update_id|reference|null: false|
# Association
- belongs_to :users

# groupテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
# Association
- has_many :messages
- has_many :groups_users
- has_many :users, through: groups_users

# messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group|reference|null: false, foreign_key: true|
|user|reference|null: false, foreign_key: true|
# Association
- belomgs_to :group
- belomgs_to :user
