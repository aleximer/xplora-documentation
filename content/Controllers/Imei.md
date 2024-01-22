### \\App\\Http\\Controllers\\Imei

ImeiApi is a standard controller which get information about IMEI and tries to match it to activation url by using [[Country middleware]] info and/or by reading `xplora.surfaces.pertner_url` database value ^surface-db

```
REQUEST 
POST /imei
Content-Type: application/x-www-form-urlencoded

imei={imei}

```

> [!info]
> If IMEI number not found or IMEI number is from WEB surface where you have to provide specific order number in order to activate, it will redirect back to `HTTP_REFERER` with query `error=imei_not_found`

