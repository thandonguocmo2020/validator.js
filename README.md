# validator.js

[![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url] [![Coveralls Status][coveralls-image]][coveralls-url] [![Downloads][downloads-image]][npm-url]


Một thư viện của xác nhận string và dọn dẹp code "ví dụ script". 


### Server-side usage

cài đtặ thư viện với  `npm install validator`

```javascript
var validator = require('validator');

validator.isEmail('foo@bar.com'); //=> true
```

#### ES6

```javascript
import validator from 'validator';
```

Hoặc bạn có thể import 1 phần của thư viện

```javascript
import isEmail from 'validator/lib/isEmail';
```

### Client-side usage

Thư viện có thể được nạp hoặc như một kịch bản độc lập, hoặc thông qua một bộ xử lý  [AMD][amd]-loader -tương thích

```html
<script type="text/javascript" src="validator.min.js"></script>
<script type="text/javascript">
  validator.isEmail('foo@bar.com'); //=> true
</script>
```

Cài đặt với  [bower][bower]

```bash
$ bower install validator-js
```

### Strings only

**Thư viện này chỉ xác nhận  "validates" and sanitizes "dọn dẹp script html hoặc javascript" chuỗi duy nhất**


Nếu bạn không chắc chắn đầu vào input là một chuỗi hãy sử dụng  `input + ''`.
Phân tích bất kỳ điều gì khác một chuỗi là một lỗi trả về.

### Validators

- **contains(str, seed)** - Kiểm tra chuỗi có bao gồm một chuỗi mẫu.
- **equals(str, comparison)** - Kiểm tra chuỗi có phù hợp với chuỗi so sánh
- **isAfter(str [, date])** - Kiểm tra chuỗi là ngày sau một ngày qui định. mặc định là hôm nay (defaults to now).
- **isAlpha(str [, locale])** -kiểm tra xem chuỗi có chứa chữ cái (a-zA-Z). Locale là một của `['ar', 'ar-AE', 'ar-BH', 'ar-DZ', 'ar-EG', 'ar-IQ', 'ar-JO', 'ar-KW', 'ar-LB', 'ar-LY', 'ar-MA', 'ar-QA', 'ar-QM', 'ar-SA', 'ar-SD', 'ar-SY', 'ar-TN', 'ar-YE', 'cs-CZ', 'da-DK', 'de-DE', 'en-AU', 'en-GB', 'en-HK', 'en-IN', 'en-NZ', 'en-US', 'en-ZA', 'en-ZM', 'es-ES', 'fr-FR', 'hu-HU', 'nl-NL', 'pl-PL', 'pt-BR', 'pt-PT', 'ru-RU', 'sr-RS', 'sr-RS@latin', 'tr-TR', 'uk-UA']`) and defaults to `en-US`.
- **isAlphanumeric(str [, locale])** -kiểm tra xem chuỗi chỉ chứa chữ cái và số . LLocale là một của `['ar', 'ar-AE', 'ar-BH', 'ar-DZ', 'ar-EG', 'ar-IQ', 'ar-JO', 'ar-KW', 'ar-LB', 'ar-LY', 'ar-MA', 'ar-QA', 'ar-QM', 'ar-SA', 'ar-SD', 'ar-SY', 'ar-TN', 'ar-YE', 'cs-CZ', 'da-DK', 'de-DE', 'en-AU', 'en-GB', 'en-HK', 'en-IN', 'en-NZ', 'en-US', 'en-ZA', 'en-ZM', 'es-ES', 'fr-FR', 'fr-BE', 'hu-HU', 'nl-BE', 'nl-NL', 'pl-PL', 'pt-BR', 'pt-PT', 'ru-RU', 'sr-RS', 'sr-RS@latin', 'tr-TR', 'uk-UA']`) and defaults to `en-US`.
- **isAscii(str)** - kiểm tra xem chuỗi chứa ký tự ASCII..
- **isBase64(str)** - kiểm tra xem một chuỗi là base64 mã hóa..
- **isBefore(str [, date])** - kiểm tra xem chuỗi là một ngày trước ngày quy định.
- **isBoolean(str)** -kiểm tra xem một chuỗi là một boolean "true hoặc false"
- **isByteLength(str, options)** - kiểm tra nếu chiều dài của chuỗi  (nằm trong bytes) có độ dài.`options` là một đối tượng mặc định  `{min:0, max: undefined}`.
- **isCreditCard(str)** - kiểm tra xem chuỗi là thẻ tín dụng.
- **isCurrency(str, options)** - kiểm tra xem chuỗi là giá trị tiền tệ hợp lệ.. `options` là một object với mặc định `{symbol: '$', require_symbol: false, allow_space_after_symbol: false, symbol_after_digits: false, allow_negatives: true, parens_for_negatives: false, negative_sign_before_digits: false, negative_sign_after_digits: false, allow_negative_sign_placeholder: false, thousands_separator: ',', decimal_separator: '.', allow_space_after_digits: false }`.
- **isDataURI(str)** - kiểm tra xem chuỗi là một [data uri format](https://developer.mozilla.org/en-US/docs/Web/HTTP/data_URIs).
- **isDate(str)** - Kiểm tra chuỗi nếu là một ngày.
- **isDecimal(str)** - kiểm tra xem chuỗi đại diện cho một số thập phân, chẳng hạn như 0.1, .3, 1.1, 1.00003, 4.0, etc.
- **isDivisibleBy(str, number)** - kiểm tra chuỗi là chia hết cho number.
- **isEmail(str [, options])** - Kiểm tra nếu string là một email. `options` là một object với các giá trị mặc định `{ allow_display_name: false, require_display_name: false, allow_utf8_local_part: true, require_tld: true }`. Nếu `allow_display_name` Là thiết lập bằng true,Các xác nhận validator có thể xác nhận phù hợp với  `tên hiển thị trong <email-address>`. Nếu `require_display_name` là được thiết lập bằng true. Các xác nhận validator có thể loại bỏ các chuỗi mà không phải bên trong định dạng `Display Name <email-address>`. Nếu `allow_utf8_local_part` được thiết lập để  false, các xác nhận validator có thể không được áp dụng với non-English UTF8 kí tự trong địa chỉ email 'local part. Nếu  `require_tld` được thiết lập là false, e-mail addresses không phải có TLD trong của domain cũng sẽ được phù hợp.

- **isEmpty(str)** - Nếu chuỗi có một chiều dài là 0;
- **isFQDN(str [, options])** - Kiểm tra chuỗi là một domain đầy đủ (e.g. domain.com). `options` nó là một object với các thiết lập mặc định `{ require_tld: true, allow_underscores: false, allow_trailing_dot: false }`.
- **isFloat(str [, options])** - Kiểm tra nếu một chuỗi là float. `options` là một object có thể chứa các `min`, `max`, `gt`, and/or `lt` để xác nhận các float nằm trong khoảng (e.g. `{ min: 7.22, max: 9.55 }`). `min` và  `max` là  tương tự đến 'greater hoặc equal' và 'less or equal', tương ứng `gt` và `lt` là giống nhau.
- **isFullWidth(str)** - Kiểm tra chuỗi khớp với chuỗi full.
- **isHalfWidth(str)** - check if the string contains any half-width chars.
- **isHexColor(str)** - check if the string is a hexadecimal color.
- **isHexadecimal(str)** - check if the string is a hexadecimal number.
- **isIP(str [, version])** - nếu các chuỗi là một địa chỉ IP (version 4 or 6).
- **isISBN(str [, version])** - check if the string is an ISBN (version 10 or 13).
- **isISSN(str [, options])** - Nếu là một tiêu chuẩn Serial Number  [ISSN](https://en.wikipedia.org/wiki/International_Standard_Serial_Number). `options`Một object tùy chọn có giá trị mặc định `{ case_sensitive: false, require_hyphen: false }`. If `case_sensitive` is true, ISSNs with a lowercase `'x'` as the check digit are rejected.
- **isISIN(str)** - check if the string is an [ISIN][ISIN] (stock/security identifier).
- **isISO8601(str)** - check if the string is a valid [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date.
- **isIn(str, values)**  Kiểm tra chuỗi có trong một mảng cho trc .
- **isInt(str [, options])** - Kiểm tra chuỗi có phải là một number integer. `options` là một object mà có thể chứa các key `min` and/or `max` để check các số trong một khoảng (e.g. `{ min: 10, max: 99 }`). `options` cũng có thể chứa các key `allow_leading_zeroes`,mà khi nào set giá trị false có thể  cấm không cho phép integer values với giá trị 0 (e.g. `{ allow_leading_zeroes: false }`). cuối cùng , `options` các tùy chọn có thể chứa  keys `gt` và/hoặc `lt` ó sẽ thực thi các số nguyên là lớn hơn hoặc nhỏ hơn, tương ứng, giá trị cung cấp (e.g. `{gt: 1, lt: 4}` for a number between 1 and 4).
- **isJSON(str)** - Check nếu giá trị có phải là chuỗi json (note: uses JSON.parse).
- **isLength(str, options)** -kiểm tra nếu chiều dài của chuỗi rơi trong một phạm vi. `options` là một object với các giá trị mặc định `{min:0, max: undefined}`. Note: this function takes into account surrogate pairs.
- **isLowercase(str)** - kiểm tra chuỗi có phải lowercase.
- **isMACAddress(str)** - kiểm tra một địa chỉ  MAC address.
- **isMD5(str)** - kiểm tra chuỗi là một mã MD5 hash.
- **isMobilePhone(str, locale)** - kiểm tra chuỗi có phải là một trong các số điện thoại, (locale là một tên với giá trị của các quốc gia `['ar-DZ', 'ar-SA', 'ar-SY', 'cs-CZ', 'de-DE', 'da-DK', 'el-GR', 'en-AU', 'en-GB', 'en-HK', 'en-IN',  'en-NG', 'en-NZ', 'en-US', 'en-CA', 'en-ZA', 'en-ZM', 'es-ES', 'fi-FI', 'fr-FR', 'he-IL', 'hu-HU', 'it-IT', 'ja-JP', 'ms-MY', 'nb-NO', 'nn-NO', 'pl-PL', 'pt-PT', 'ru-RU', 'sr-RS', 'tr-TR', 'vi-VN', 'zh-CN', 'zh-TW']`).
- **isMongoId(str)** -  kiểm tra xem chuỗi là một đại diện hex-mã hóa giá trị của một OBJECT ID của [MongoDB ObjectId][mongoid].
- **isMultibyte(str)** - iểm tra xem chuỗi có chứa một hoặc nhiều ký tự multibyte.
- **isNumeric(str)** - kiểm tra xem chuỗi có chứa numbers.
- **isSurrogatePair(str)** - kiểm tra chuỗi xem có bất kỳ kí tự đại diện.
- **isURL(str [, options])** - kiểm tra chuỗi có phải là một url  `options` có giá trị là một object `{ protocols: ['http','https','ftp'], require_tld: true, require_protocol: false, require_host: true, require_valid_protocol: true, allow_underscores: false, host_whitelist: false, host_blacklist: false, allow_trailing_dot: false, allow_protocol_relative_urls: false }`.
- **isUUID(str [, version])** - kiểm tra chuỗi có phải là một uuid UUID (version 3, 4 or 5).
- **isUppercase(str)** - kiểm tra chuỗi có phải là uppercase.
- **isVariableWidth(str)** - check if the string contains a mixture of full and half-width chars.
- **isWhitelisted(str, chars)** - kiểm tra các kí tự có trong danh sách không cho phép backlish từ 
- **matches(str, pattern [, modifiers])** - kiểm tra chuỗi có phù hợp với   pattern. cả hai `matches('foo', /foo/i)` hoặc `matches('foo', 'foo', 'i')`.

### Sanitizers

Loại bỏ các kí tự mã. 


- **blacklist(input, chars)** - xóa bỏ các kí tự có trong backlist từ đầu vào `blacklist(input, '\\[\\]')`.

- **escape(input)** - replace `<`, `>`, `&`, `'`, `"` and `/` with HTML entities.
- **unescape(input)** - thay thế các thực thể HTML mã hóa với `<`, `>`, `&`, `'`, `"` and `/`.
- **ltrim(input [, chars])** - cắt ký tự từ bên trái của đầu vào.
- **normalizeEmail(email [, options])** - canonicalizes an email address. `options` is an object with the following keys and default values:
  - *all_lowercase: true* - Transforms the local part (before the @ symbol) of all email addresses to lowercase. Please note that this may violate RFC 5321, which gives providers the possibility to treat the local part of email addresses in a case sensitive way (although in practice most - yet not all - providers don't). The domain part of the email address is always lowercased, as it's case insensitive per RFC 1035.
  - *gmail_lowercase: true* - GMail addresses are known to be case-insensitive, so this switch allows lowercasing them even when *all_lowercase* is set to false. Please note that when *all_lowercase* is true, GMail addresses are lowercased regardless of the value of this setting.
  - *gmail_remove_dots: true*: Removes dots from the local part of the email address, as GMail ignores them (e.g. "john.doe" and "johndoe" are considered equal).
  - *gmail_remove_subaddress: true*: Normalizes addresses by removing "sub-addresses", which is the part following a "+" sign (e.g. "foo+bar@gmail.com" becomes "foo@gmail.com").
  - *gmail_convert_googlemaildotcom: true*: Converts addresses with domain @googlemail.com to @gmail.com, as they're equivalent.
  - *outlookdotcom_lowercase: true* - Outlook.com addresses (including Windows Live and Hotmail) are known to be case-insensitive, so this switch allows lowercasing them even when *all_lowercase* is set to false. Please note that when *all_lowercase* is true, Outlook.com addresses are lowercased regardless of the value of this setting.
  - *outlookdotcom_remove_subaddress: true*: Normalizes addresses by removing "sub-addresses", which is the part following a "+" sign (e.g. "foo+bar@outlook.com" becomes "foo@outlook.com").
  - *yahoo_lowercase: true* - Yahoo Mail addresses are known to be case-insensitive, so this switch allows lowercasing them even when *all_lowercase* is set to false. Please note that when *all_lowercase* is true, Yahoo Mail addresses are lowercased regardless of the value of this setting.
  - *yahoo_remove_subaddress: true*: Normalizes addresses by removing "sub-addresses", which is the part following a "-" sign (e.g. "foo-bar@yahoo.com" becomes "foo@yahoo.com").
  - *icloud_lowercase: true* - iCloud addresses (including MobileMe) are known to be case-insensitive, so this switch allows lowercasing them even when *all_lowercase* is set to false. Please note that when *all_lowercase* is true, iCloud addresses are lowercased regardless of the value of this setting.
  - *icloud_remove_subaddress: true*: Normalizes addresses by removing "sub-addresses", which is the part following a "+" sign (e.g. "foo+bar@icloud.com" becomes "foo@icloud.com").
- **rtrim(input [, chars])** - xóa bỏ các kí tự từ bên phải của chuỗi đầu vào tìm thấy
- **stripLow(input [, keep_new_lines])** - xóa bỏ các kiw tự với các vị trí số < 32 and 127, chủ yếu là kiểm tra nhân vật. Nếu `keep_new_lines` là `true`, ký tự xuống dòng được bảo quản (` \ n` và `\ r`, hex` 0xA` và `0xD`). Unicode-an toàn trong JavaScript.
- **toBoolean(input [, strict])** - chuyển đổi các chuỗi đầu vào cho một boolean. Tất cả mọi thứ trừ `'0'`, `'false'` and `''` returns `true`. Trong chế độ nghiêm ngặt chỉ `'1'` and `'true'` return `true`.
- **toDate(input)** - chuyển đổi các chuỗi đầu vào đến một ngày  hoặc  `null` nếu đầu vào không phải là một date.
- **toFloat(input)** - chuyển đổi các chuỗi đầu vào cho một float, hoặc `NaN` nếu input đầu vào không phải float.
- **toInt(input [, radix])** - chuyển đổi các chuỗi đầu vào cho một integer, hoặc `NaN` nếu đầu vào không phải một integer.
- **trim(input [, chars])** - (khoảng trắng theo mặc định) từ cả hai bên của đầu vào.
- **whitelist(input, chars)** - loại bỏ ký tự không xuất hiện trong list . Các nhân vật được sử dụng trong một biểu thức chính quy và do đó bạn sẽ cần phải thoát khỏi một số ký tự đặc biệt ví dụ , e.g. `whitelist(input, '\\[\\]')`.

### XSS Sanitization

XSS sanitization was removed from the library in [2d5d6999](https://github.com/chriso/validator.js/commit/2d5d6999541add350fb396ef02dc42ca3215049e).

For an alternative, have a look at Yahoo's [xss-filters library](https://github.com/yahoo/xss-filters) or at [DOMPurify](https://github.com/cure53/DOMPurify).

### Tests

```sh
$ npm test
```

### Reading

Remember, validating can be troublesome sometimes. See [A list of articles about programming assumptions commonly made that aren't true](https://github.com/jameslk/awesome-falsehoods).

### License (MIT)

```
Copyright (c) 2016 Chris O'Hara <cohara87@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```

[downloads-image]: http://img.shields.io/npm/dm/validator.svg

[npm-url]: https://npmjs.org/package/validator
[npm-image]: http://img.shields.io/npm/v/validator.svg

[travis-url]: https://travis-ci.org/chriso/validator.js
[travis-image]: http://img.shields.io/travis/chriso/validator.js.svg

[coveralls-url]: https://coveralls.io/r/chriso/validator.js
[coveralls-image]: http://img.shields.io/coveralls/chriso/validator.js/master.svg

[amd]: http://requirejs.org/docs/whyamd.html
[bower]: http://bower.io/

[mongoid]: http://docs.mongodb.org/manual/reference/object-id/
[ISIN]: https://en.wikipedia.org/wiki/International_Securities_Identification_Number
