# app > config

Path: metadata > app > config.

Application config definitions.

## params

*Object.<string, Object\>\>*

Parameters. A name => params map.

Example:

```json
{

    "params": {
        "smtpPassword": {
            "level": "internal"
        },
        "awsS3Storage": {
            "level": "system"
        }
    }
}
```

### level

*string*

Defines availability of the config parameter in the front-end. Possible values:

* `global` – available even before logging in;
* `system` – never available;
* `internal` – never available for read, admin can write (useful for passwords, secrets) (as of v7.3);
* `admin` – available only for admin (read and write);
* `superAdmin` – available only for super-admin (read and write).

## entityTypeListParamList

*string[]*

A list of config parameters values of which are arrays of entity types. Needed to let the application know what params need to be filtered to remove entity types not available for a user.
