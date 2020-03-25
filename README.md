# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# Chat-Space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string||
|email|string||
### Association
- has_many :messages
- has_many :groups , through: :groups_users
- has_many :groups_users

## gorupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :messages
- has_many :users, through: :groups_users
- has_many :groups_users

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|message|text|null: false|
|image|string|null: false|
|user_messages_id|integer|null: flase,foreign_key: true|
|group_messages_id|integer|null: flase, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false , foreign_key: true|
|group_id|integer|null: flase, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group
