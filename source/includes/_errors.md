# Errors

<aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside>

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is badly formed
401 | Unauthorized -- Your API key is wrong
403 | Forbidden -- You do not have permission to access that device
404 | Not Found -- The specified device could not be found
405 | Method Not Allowed -- You tried to access a device with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
429 | Too Many Requests -- You're requesting too many kittens! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
