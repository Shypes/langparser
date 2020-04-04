# @shypes/language-translator

[![npm (scoped)](https://img.shields.io/npm/v/@shypes/language-translator.svg)](https://www.npmjs.com/package/@shypes/language-translator)
[![GitHub issues](https://img.shields.io/github/issues/Shypes/language-translator)](https://img.shields.io/github/issues/Shypes/language-translator)

This is a simple node.js langusge parse to help with language translation

## Install

```$
npm install @shypes/language-translator
```

## Usage

Follow the set by step guide below

## Language Folder Setup

Create a dedicated folder to store your language template file.

Default folder is `lang/src`

Create the different sample files below in the language folder

ar.json

```json
{
    "success": "نجاح",
    "email_phone_validation": "لا يمكن أن يكون البريد الإلكتروني والهاتف فارغين",
    "something_went_wrong": "هناك خطأ ما!",
    "missing_required_validation": "الحقول المطلوبة مفقودة",
    "missing_truck": "تم تعيين تجمع طلبات الشاحنات بالفعل على ${status}",
    "deliver_code":"مرحبًا ${name} ، إليك رمز otp ${code}"
}
```

en.json

```json
{
    "success": "Success!",
    "email_phone_validation": "Email and phone cannot be empty",
    "something_went_wrong": "Something went wrong!",
    "missing_required_validation": "Missing required fields",
    "missing_truck": "Truck Request Pool has already been set to ${status}", 
    "deliver_code":"Hello ${name}, here is your otp code ${code}"
}
```

## Initilaise the Application

```js
const Language = require("@shypes/language-translator");

const Lang = Language();

```

## Some Basic Configuration - Optional

```js

// set your base directory

Lang.setBaseDir("./"));

// set your base directory

Lang.setLanguageDir('src/lang');

// set your default language

Lang.setDefaultLang('en');


```

## Translation begin here

```js
// set the language in which you need

Lang.setActiveLang('ar');

// get the text base on the defined language key

translated = Lang.translate('email_phone_validation')

translated.then((text) =>{
   console.log(text);
});

```

Other Optional Method

```js

// set the extention for yout language file, default is .json

Lang.setExtention(".txt");

```

In line Langauge Loading Supported, this help you load your language data directly with a file

```js

// Tell the application to not try and load from file, optiona

Lang.setLoadFromFile(false);

const data = {
    "success": "نجاح",
    "email_phone_validation": "لا يمكن أن يكون البريد الإلكتروني والهاتف فارغين",
    "something_went_wrong": "هناك خطأ ما!",
    "missing_required_validation": "الحقول المطلوبة مفقودة",
    "missing_truck": "تم تعيين تجمع طلبات الشاحنات بالفعل على ${status}",
    "positioned": "وضعه",
    "in-premise": "في الفرضية",
    "loaded": "محمل",
    "transporting": "نقل",
    "At-destination": "في الوجهة",
    "offloaded": "تفريغها",
    "returningContainer": "حاوية عائدة",
    "delivered": "تم التوصيل",
    "deliver_code":"مرحبًا ${name} ، إليك رمز otp ${code}"
}

Lang.loadLanguage('ar', data);

```

## Dynamic language template

It also support templated json strings


```json
{
    "deliver_code":"مرحبًا ${name} ، إليك رمز otp ${code}"
}
```

```js

translated = Lang.translate('deliver_code', {'name':"John", 'code': 343923} )

translated.then((text) =>{
   console.log(text);
});
```

Output:

```json

مرحبًا John ، إليك رمز otp 343923

```


Check out the [sample files](https://github.com/Shypes/language-translator/tree/master/test) in the test directory

## License

[MIT](LICENSE) © Tosin Adesipe
