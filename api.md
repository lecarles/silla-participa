# REQUEST
https://sillaparticipa.com/2020/api/form/register

## GET
| Field  | Type    |       |
|--------|---------|-------|
| lang   | String  | va,es |

## POST
| Field  | Type    | Range |
|--------|---------|-------|
| s1q1   | Number  | 1-9   |
| s2q1   | String  |       |
| s2q2   | Number  |       |
| s2q3   | Boolean |       |
| s2q4   | Number  |       |
| s2q5   | Number  | 1-4   |
| s2q6   | Number  | 1-3   |
| s2q7   | Number  |       |
| s2q8   | Boolean |       |
| s2q9   | Boolean |       |
| s2q10  | Boolean |       |
| s3q1   | Number  | 1-5   |
| s3q2   | Number  |       |
| s3q3   | Boolean |       |
| s3q4   | Number  |       |
| s3q5   | Number  | 1-3   |
| s3q6x1 | Number  | 1-2   |
| s3q6x2 | Boolean |       |
| s3q6x3 | Number  |       |
| s3q7   | Number  |       |
| s3q8   | Boolean |       |
| s3q9   | Boolean |       |
| s3q10  | Boolean |       |
| s3q11  | Number  |       |

* Els booleans han de ser un 0 per a false i 1 per a true

# RESPONSE
## 200 OK

```
{
    "success": true
}
```

## 422 Unprocessable Entity

```
{
    "success": false,
    "errors": {
        "s2q1": "El camp 'Situacions Personals' és obligatori.",
        "s2q2": "El camp 'En quin carrer vius' és obligatori.",
        "ip:" "Has excedit el nombre d'enviaments per IP."
    }
}
```
