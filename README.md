---- start / stop docker ----
- docker-compose up
- docker-compose up -d
- docker-compose stop

---- delete docker container ----
- docker-compose down

---- connect to docker ----
- docker exec -it mage-php bash
- composer install
- php bin/magento setup:store-config:set --base-url="http://localhost:8090/"
- php bin/magento setup:store-config:set --base-url-secure="https://localhost:8090/"
- php bin/magento cache:flush
- bin/magento setup:static-content:deploy -f
- chgrp -R www-data *
- chmod -R 775 *

---- DB Config ----
- Host:   mage-mysql
- User:   root
- Passw:  


