
First action, do this http request, after put basic account information

`POST : https://mds-vip-staging.moveo.net/vip-app/sendRegistrationsCodes`

```json
{
  "first_name": "Gaston",
  "last_name": "Graciani",
  "email": "gaston@moveo.net",
  "mobile_phone": "+1 272-845-9670",
  "photo_url": "",
  "captcha": "long-captcha-token"
}
```


After that, in the db is generate the record on the `account_pre_registratrions` table with that data.

second step, is validate email, should receive on your inbox a code that you put on the GUI and do the following http request

`POST : https://mds-vip-staging.moveo.net/vip-app/validateEmailRegistrationCode`

```json
{
  "captcha": "long-captcha-token",
  "email_validation_code": "49869",
  "pre_registration_hash": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhY2NvdW50X3JlZ2lzdHJhdGlvbl9pZCI6MjYwOH0.d15glbg22gpyzRan_LtklTsZk2Ch7vVyk0Ejsykycbk"
}
```

After that step, the third step is to validate mobile phone, should receive a code via SMS and put on the GUI, doing this http request

`POST : https://mds-vip-staging.moveo.net/vip-app/validatePhoneRegistrationCode`

```json
{
  "captcha": "long-captacha-token",
  "phone_validation_code": "11244",
  "pre_registration_hash": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhY2NvdW50X3JlZ2lzdHJhdGlvbl9pZCI6MjYwOH0.d15glbg22gpyzRan_LtklTsZk2Ch7vVyk0Ejsykycbk"
}
```

**Note**: the pre registration hash is generate on the backend when do the first http request.

After that, we select account type (personal or company) and we set a password doing the following http request

`POST : https://mds-vip-staging.moveo.net/vip-app/register`

```json
{
  "first_name": "Gaston",
  "last_name": "Graciani",
  "email": "gaston@moveo.net",
  "mobile_phone": "+1 272-845-9670",
  "address": "",
  "address_details": "",
  "address_city": "",
  "address_state": "",
  "address_country": "",
  "address_zipcode": "",
  "address_lat": null,
  "address_lng": null,
  "company_name": "",
  "is_company": false,
  "username": "",
  "password": "MoveoRevolution2023!",
  "re_password": "MoveoRevolution2023!",
  "pre_registration_hash": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhY2NvdW50X3JlZ2lzdHJhdGlvbl9pZCI6MjYwOH0.d15glbg22gpyzRan_LtklTsZk2Ch7vVyk0Ejsykycbk",
  "captcha": "long-captcha-token"
}
```

