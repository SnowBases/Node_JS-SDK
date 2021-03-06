## Seamlesss Integration with Node.js

### Pre-Requisite
1. Node Js installed(preferably latest version)
2. Install package md5
3. Install package request
4. Install package express
5. Install package body-pareser
6. MOLPay Development or Production ID.
7. MOLPay General API.

For ease of use, a demo version has been uploaded along with a sample html file and all required node modules in a zip file.
If there is any trouble in using the uploaded package modules, the packages can be easily installed on windows via npm install <packagename> 
or you can just refer here https://www.npmjs.com/ .

  
### Installation
1. Download the app.js file
2. Put app.js file in same directory with your project files.
3. Open command prompt terminal,locate destination of app.js.
4. Install all neccesary depencies via ```npm install```
5. Remember to change name inside app.js of 'index.html' to your own html page. (There is only 1 line with index.html)
6. Run 'node app.js' to execute file.
7. Open localhost based on given localhost server to access your web page.

**IMPORTANT: Remember to register your website server address or localhost address with MOLPay in advance so that you can access other payment channels for sandbox testing

### Set Environment
Set which type of enviroment to use with either sandbox or production
```Javascript
var enviroment = "sandbox" or "production"
```
For the html demo, set the environment using the following links.

For sandbox:
```html
<script src="https://sandbox.molpay.com/MOLPay/API/seamless/3.16/js/MOLPay_seamless.deco.js"></script>
```

For  production
```html
<script src="https://www.onlinepayment.com.my/MOLPay/API/seamless/3.17/js/MOLPay_seamless.deco.js">
```
### Set variables
Insert values into these variables:
```Javascript
var merchant_id = "";//Insert merchant id here
var orderid = ""; // Order ID should be random generated by merchant function
var vkey = "*************"; //Replace ********** with your MOLPay verification_Key
var secret_key = "***********";//Replace ********** with your MOLPay Private Secret_Key
```
*Note: orderid should be defined by merchant function. Hardcoding method is used for convenience of testing

### Prepare Payment object detail
```Javascript
        status = true;// Set True to proceed with MOLPay
        mpsmerchantid = merchant_id;
        mpschannel = req.body.payment_options;
        mpsamount = req.body.total_amount;
        mpsorderid = orderid; //Order ID should be a random generated value by merchant
        mpsbill_name = req.body.billingFirstName + " " + req.body.billingLastName;
        mpsbill_email = req.body.billingEmail;
        mpsbill_mobile = req.body.billingMobile;
        mpsbill_desc = req.body.billingAddress;
        mpscountry  = "MY";
        mpsvcode  = md5(req.body.total_amount + merchant_id + orderid + vkey);
        mpscurrency = req.body.currency;
        mpslangcode = "en";
        mpstimer = req.body.molpaytimer;
        mpstimerbox = "#counter";
        mpsreturnurl = "http://127.0.0.1:8080/returnurl"; // Enter your return url here
        mpscancelurl = "http://127.0.0.1:8080/cancelurl"; // Enter your cancel url here
        mpsapiversion = "3.16"; //**NOTE:  For production use '3.17' / Sandbox use '3.16'
```

Please request merchant ID and vkey from Merchant Technical Support / Customer Care : support@molpay.com . The order ID can be anything.
