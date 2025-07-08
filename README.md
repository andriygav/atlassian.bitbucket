# Atlasian Bitbucket Setup

To deploy own bitbucket you need make several actions.

## Run bitbucket

### Pull current repository:
```
git clone --recurse-submodules https://github.com/andriygav/atlassian.bitbucket.git
```

### Change some data in the deploy
1. Change deploy/docker-compose.yaml. Replace `bitbucket.domain.com` to your own domain name.
2. Change deploy/docker-compose.yaml. Replace `/mnt/bitbucket/bitbucket-data` and `/mnt/bitbucket/bitbucket-db-volume` to the place where the data must be stored.
3. Change deploy/nginx.com. Replace `bitbucket.domain.com` to your own domain name.
4. Change deploy/ssl/. Setup your certificate for domain in `cert.pem` file and key to the `key.pem`.

### Run all
```
docker compose -f deploy/docker-compose.yaml up -d
```

## Setup Bitbucket
For crack bitbucket we are using [AtlassianCrack](https://github.com/IAlexEgorov/AtlassianCrack). After starting run down next code:
```
nano license_key_bitbucket.txt # For change to our licence ID from the browser
php atlassian-keygen.php -e license_key_bitbucket.txt # Given Licence Key use in the browser
```