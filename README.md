# regex-to-understand-cpanel-logs

This document provides a description for a regular expression designed to match URLs with the following structure:

```
protocol://domain:port:username:password
```

## Regular Expression Pattern

```regex
^(https?):\/\/([a-zA-Z0-9\.\-]+):(\d+):([a-zA-Z0-9\-_\+]+):([a-zA-Z0-9\-_\+]+)$
```

## Explanation

1. `^(https?)`: Matches the protocol, which can be either `http` or `https`.
   - `^` asserts the position at the start of the string.
   - `(https?)`: Matches either `http` or `https`.
       - `s?`: The `s` is optional, allowing for both `http` and `https`.

2. `:\/\/`: Matches the literal string `://`.

3. `([a-zA-Z0-9\.\-]+)`: Matches the domain, which can include:
   - Alphanumeric characters (`a-zA-Z0-9`)
   - Dots (`.`)
   - Hyphens (`-`)

4. `:(\d+)`: Matches a colon followed by one or more digits (the port).
   - `:`: Matches the literal colon character.
   - `(\d+)`: Matches one or more digits (`0-9`).

5. `:([a-zA-Z0-9\-_\+]+)`: Matches a colon followed by one or more alphanumeric characters, hyphens, underscores, or plus signs (the username).
   - `:`: Matches the literal colon character.
   - `([a-zA-Z0-9\-_\+]+)`: Matches one or more of the following characters:
       - Alphanumeric characters (`a-zA-Z0-9`)
       - Hyphens (`-`)
       - Underscores (`_`)
       - Plus signs (`+`)

6. `:([a-zA-Z0-9\-_\+]+)$`: Matches a colon followed by one or more alphanumeric characters, hyphens, underscores, or plus signs (the password) until the end of the string.
   - `:`: Matches the literal colon character.
   - `([a-zA-Z0-9\-_\+]+)`: Matches one or more of the following characters:
       - Alphanumeric characters (`a-zA-Z0-9`)
       - Hyphens (`-`)
       - Underscores (`_`)
       - Plus signs (`+`)
   - `$`: Asserts the position at the end of the string.

## Examples

### Valid Matches
- `http://example.com:8080:user-123:pass_word+123`
- `https://my-domain.org:443:username:password`

### Invalid Matches
- `ftp://example.com:8080:user:pass` (Invalid protocol)
- `http://example.com:port:user:pass` (Port is not numeric)

This regular expression pattern ensures that URLs conforming to the specified structure are accurately matched.
