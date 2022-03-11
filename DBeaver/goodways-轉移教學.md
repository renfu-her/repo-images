goodways 轉移教學
===

###### tags: `柏榮數位整合`

## 伺服器
- 192.53.116.194 

## ssh 登入伺服器，二選一
- ssh c:\.ssh\id_rsa amiwu@192.53.116.194 
    - 密碼：WoyurphC6k4X2VSY
- ssh c:\.ssh\id_rsa zivhsiao@192.53.116.194
    - 密碼： i8XwKjuOW70Tb6H4

- mariaDB 賬號密碼
    - amiwu /86dMZzJd1bJOk0m2
    - zivhsiao / 86dMZzJd1bJOk0m2

## 確定網域，假設 demo.com.tw
要先增加一個 demo 的資料夾
```
sudo su
密碼使用上面就可以

mkdir /var/www/html/網域
- 網域指的是 demo 就可以了
```

## FileZilla 上傳檔案
建立一個名稱 demo
- 一般設定
    - 協定：SFTP
    - 主機：192.53.116.194
    - 登入形式：金鑰檔案
    - 使用者：zivhsiao
    - 金鑰檔案：d:\.goodways_ssh\id_rsa
- 進階設定
    - 預設本地目録
        - 直接瀏覽實際存放的目録
    - 預設遠端目録
        - /var/www/html/demo
    - 使用同步瀏覽打勾
- 直接檔案上傳就可以了
- 記得 .htaccess, wp-content 這兩個都要設定成 777
    - cmd 直接 ssh 後端主機
        - chmod -R 777 wp-content
        - chmod 777 .htaccess
    - 或者直接用 FileZilla 直接修改
        - 記得要選擇“子目録以及檔案”就可以了

## 資料庫
- 使用 DBeaver
- 安裝
    - [直接從這裏下載並且安裝](https://dbeaver.io/download/)
    - 安裝完成，直接啓動
    - 然後參照下面的項目進行
    - 設定連結的資料庫
        - ssh 一定先設定
        - ![](https://raw.githubusercontent.com/renfu-her/repo-images/main/DBeaver/dbeaver-connection-1.png)
        - 再來是主要 
        - ![](https://raw.githubusercontent.com/renfu-her/repo-images/main/DBeaver/dbeaver-connection-2.png)
    - 連綫資料庫
        - ![](https://raw.githubusercontent.com/renfu-her/repo-images/main/DBeaver/dbeaver-db-1.png)
    - 點擊"數據庫"，滑鼠右鍵 -> 新建資料庫
        - ![](https://raw.githubusercontent.com/renfu-her/repo-images/main/DBeaver/create-database.png)
    - 填入你的資料庫名稱
- 導入 SQL
    - 針對你的資料庫，按下右鍵 -> 工具 -> 執行腳本
    - ![](https://raw.githubusercontent.com/renfu-her/repo-images/main/DBeaver/import-sql.png)
- 完成匯入的動作

## 修改 DB 的資料
- 修改
    - define('DB_NAME', '資料庫名稱');
    - define('DB_USER', 'zivhsiao');
    - define('DB_PASSWORD', '86dMZzJd1bJOk0m2');
    - define('DB_HOST', 'localhost');
- 增加一項
    - define('FS_METHOD', 'direct');

這樣就設置完成
