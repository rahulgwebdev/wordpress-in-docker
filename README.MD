# Next Steps
## 1) Download WordPress
You can download [WordPress](https://wordpress.org/latest.tar.gz)
 manually and then extract its contents to the 'src' folder. Alternatively, you can use the following command within the repository folder:

```    
# Download WordPress archive
wget -O wordpress.tar.gz https://wordpress.org/latest.tar.gz

# Create the 'src' directory if it doesn't exist
mkdir -p src

# Extract the contents of the downloaded archive to the 'src' directory
tar -xf wordpress.tar.gz -C src --strip-components=1

# Remove the downloaded archive file
rm -rf wordpress.tar.gz
```


### 2) Set the 'www-data' User Group
To ensure that the 'www-data' user group has the appropriate permissions, use the following command:
```
sudo chown -R www-data:www-data ./src/wp-content
```

### 3) Rename wp-config-sample.php to wp-config.php
```
# You can use this commands
mkdir -p src
cd ./src/
mv wp-config-sample.php wp-config.php
cd ..
```

### 4) Make the Following Changes in 'wp-config.php'
These changes are necessary to enable plugin installation and configure the database settings:

```
// ** these two lines required to install plugins  ** //
define( 'FS_METHOD', 'direct' );
define( 'UPLOADS', 'wp-content/uploads' );

// ** Database settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define( 'DB_NAME', 'wordpress' );

/** Database username */
define( 'DB_USER', 'wordpress' );

/** Database password */
define( 'DB_PASSWORD', 'wordpresspassword' );

/** Database hostname */
define( 'DB_HOST', 'mariadb' );
```

### 5) Build and start the containers

```
# prefix sudo if needed
docker-compose up --build
# open the following url on http://localhost
```
### 6) (optional) open phpMyAdmin (mysql client)
    username - root
    password - rootpassword
    # http://localhost:8085
