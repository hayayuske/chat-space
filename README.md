# chat-space DB設計  
***  
## messages table  
 - カラム  
   - text :body  
   - string :image  
   - timestamps null: false  
   - references :user, foreign_key: true  
   - references :group, foreign_key: true  
 - アソシエーション  
   - belongs_to :user  
   - belongs_to :group  

## users table  
 - カラム  
   - string :name, null: false  
   - text :email, unique: true  
   - text :password, null: false  
   - references :group, foreign_key: true, index: true  
 - アソシエーション  
   - has_many :messages  
   - has_many :groups_users  
   - has_many :groups, through: :groups_users  

## groups table  
 - カラム  
   - string :groupname, unique: true  
 - アソシエーション  
   - has_many :groups_users  
   - has_many :users, through: :groups_users  

## membership table  

 - カラム  
   - references :user, foreign_key: true  
   - references :group, foreign_key: true  
 - アソシエーション  
   - belogs_to :group  
   - belogs_to :user  

