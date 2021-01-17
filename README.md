## usersテーブル

|Colum                    |Type        |Options                         | 
|-------------------------|------------|--------------------------------|
|name                     |string      |null: false                     |
|email                    |string      |null: false, unique: true       |
|encrypted_password       |string      |null: false                     |
|team_id                  |references  |null: false, foreign_key: true  |
### Association

has_many teams
has_many team_users
has_many posts
has_many comments





## team_usersテーブル

|Colum                    |Type       |Options                          | 
|-------------------------|-----------|---------------------------------|
|user_id                  |references |null: false, foreign_key: true   |
|team_id                  |references |null: false, foreign_key: true   |

### Association
belongs_to user
belongs_to team





## teamsテーブル

|Colum                    |Type       |Options                          | 
|-------------------------|-----------|---------------------------------|
|name                     |string     |null: false                      |
|user_id                  |references |null: false, foreign_key: true   |


### Association
has_many users
has_many team_users
has_many posts








## postsテーブル

|Colum                    |Type       |Options                          | 
|-------------------------|-----------|---------------------------------|
|date                     |date       |null: false                      |
|text                     |text       |null: false                      |
|user_id                  |references |null: false, foreign_key: true   |
|team_id                  |references |null: false, foreign_key: true   |

### Association
belongs_to user
belongs_to team
has_many comments








## commentsテーブル

|Colum                    |Type       |Options                          | 
|-------------------------|-----------|---------------------------------|
|text                     |text       |null: false                      |
|user_id                  |references |null: false, foreign_key: true   |
|post_id                  |references |null: false, foreign_key: true   |

### Association
belongs_to user
belongs_to post
has_many comments