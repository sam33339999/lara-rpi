# raspberry-php
raspberry pi with docker -> arm version



### PHP-FPM
- bcmath - 精度數學運算
- calendar - 日歷運算
- dba - Database (dbm-style) Abstraction Layer) 可以串接 ORACLE's Berkeley DB ， 相容的DB [dba-ext](https://www.php.net/manual/en/dba.requirements.php)
- exif - Exchangeable image information 實際上Exif格式就是在JPEG格式頭部插入了數碼照片的資訊，包括拍攝時的光圈、快門、白平衡、ISO、焦距、日期時間等各種和拍攝條件以及相機品牌、型號、色彩編碼、拍攝時錄製的聲音以及全球定位系統（GPS）、縮圖等。簡單地說，Exif=JPEG 拍攝引數。因此，你可以利用任何可以檢視JPEG檔案的看圖軟體瀏覽Exif格式的照片，但並不是所有的圖形程式都能處理Exif資訊。
- gd - 處理圖片的擴充庫
- gettext - 本地語言化讀取擴充庫
- imagick - ImageMagick 擴充，與 GD 相比，產生的圖片及質量或許可能比較高(?, 代價: 圖片可能會比較大一些) 且複雜操作 imagick 可以比 gd 方便做到，另一方面， ImageMagick 可能不像 GD 那樣受到大多主機供應商的支持，所以你會增加一個相當大的依賴性。
- memcached - 一個緩存工具的函示庫
- mysqli
- opcache ... `zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20170718/opcache.so`
- pcntl
- pdo
- pdo_mysql
- shmop - 一個易於使用的函式庫，允許 PHP 讀取、寫入、創建、刪除 Unix 共享內存段 
- sockets
- sodium - 一個比較現代、抽象的一個庫，用於加密、解密、簽名、密碼散列等等... 目標為提供建立更高級別的加密工具所需的核心操作 

- > sysvsem, sysvshm, sysvmsg ， PHP 有一族函式，是 Unix 的 V IPC 函數族的包裝，他們很少被使用到，但是他們很強大！
- sysvmsg
- sysvsem
- sysvshm

- zip 


- jit
