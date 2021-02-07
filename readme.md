
# PasswordHashExample

A Synergy .NET Core example of how to go about hashing passwords for safe storage, and also how to subsequently validate user-supplied passwords against the stored hashed value.

This example uses a random salt value to increase the strenght of the hashed result, and a different and random salt value is used each time a password is hashed. This means that if you hash the same password yuu will get different results each time!

This is achieved by returning both the salt value and hashed password value as a combined, base-64 encoded string that is easy to handle and store. The length of the returned string is always 48 bytes.

An example of hashing a password:

```
    data password = "Very$secure_password"
    data hashedPassword = new Services.Security.PasswordSecurity().HashPassword(password)
```

An example of comparing a password agaist a previously hashed value:

```
    data candidatePassword = "hackme$123"
    data booleanresult = new Services.Security.PasswordSecurity().CheckPassword(candidatePassword,hashedPassword)
```
