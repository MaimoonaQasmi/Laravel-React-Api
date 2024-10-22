# Laravel-React-API

## 🐞 Error:  
When trying to log in using the `Login.jsx` component, you may encounter the following issue:

```bash
POST http://localhost:8000/login 419 (unknown status)
```

In the console, you might see this Axios error:

```javascript
AxiosError {
  message: 'Request failed with status code 419',
  name: 'AxiosError',
  code: 'ERR_BAD_REQUEST',
  config: {…},
  request: XMLHttpRequest, 
  …
}
```

![Error Screenshot](https://github.com/user-attachments/assets/b4d850e1-324c-4e3f-945f-177928613986)

---

## 💡 Solution:  
To resolve this issue, you need to adjust the CSRF token validation in your Laravel application. 

For **Laravel 11**, modify the `bootstrap/app.php` file by adding the following code:  

```php
$middleware->validateCsrfTokens(except: [
    '*'
]);
```

This will bypass CSRF validation for all routes, ensuring that your login request is accepted during development.

![Solution Screenshot](https://github.com/user-attachments/assets/f453fbc9-6022-45c4-96ea-f0f5abf540d2)

---
