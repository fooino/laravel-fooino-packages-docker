### Docker compose sample file for running and testing the fooino laravel packages

```bash
git clone https://github.com/fooino/laravel-fooino-packages-docker.git

cd ./laravel-fooino-packages-docker

docker-compose -p fooino up -d --build

docker exec -it fooino-php bash

cd ../PACKAGE_NAME

composer update

./vendor/bin/pest
exit
```