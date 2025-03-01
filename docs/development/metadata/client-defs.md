# clientDefs

Path: metadata > clientDefs > {Scope}

Contains parameters used by the front-end.

## controller

*string*

Defines a client controller class.

## collection

*string*

Defines a client record collection class. Optional.

The default value: `'collection'`. Corresponds to the path `client/src/collection.js`.

## model

*string*

Defines a client record model class. Optional.

## acl

*string*

Defines a client acl class. Optional.

The default value: `'acl'`. Path `client/src/acl.js`.

## aclPortal

*string*

Defines a client acl class for portals. Optional.

The default value: `'acl-portal'`. Path `client/src/acl-portal.js`.

## createDisabled

*boolean*

Allows to disable the ability to create entity from user interface (from the list view).

## searchPanelDisabled

*boolean*

Allows to hide a search panel on the list view.


## views

Custom view classes for list, detail, edit.

Example:

```
{
    "list": "custom:views/test/list",
    "detail": "custom:views/test/detail"
}
```

## recordViews

Custom record view classes. For list, detail, edit, detailQuick, editQuick, kanban, listRelated.

Example:
```
{
    "list": "custom:views/test/record/list"
}
```

## modalViews

Modal view classes.

Example:
```
{
    "detail": "custom:views/test/modal/detail",
    "select": "custom:views/test/modal/select-records"
}
```

## exportDisabled

*boolean*

Disable the *export* mass-action.

## massUpdateDisabled

*boolean*

Disable the *mass-update* mass action.

## massRemoveDisabled

*boolean*

*As of v7.4.*

Disable the *remove* mass action.

## massFollowDisabled

*boolean*

Disable the *follow* mass-action.

## convertCurrencyDisabled

*boolean*

Disable the *convert-currency* mass-action and action.

## mergeDisabled

*boolean*

Disable the record merge functionallity.


## filterList

A list of primary filters.

Exanmple:

```json
{
    "filterList": [
        {
            "name": "planned"
        },
        {
            "name": "held",
            "style": "success"
        },
        {
            "name": "todays"
        }
    ]
}
```

## boolFilterList

A list of bool filters.

Example:

```json
{
    "boolFilterList": ["onlyMy"]
}
```

## defaultFilterData

A default filter data.

## selectDefaultFilters

Used as a default set filter on the select-records modal.

```json
{
    "selectDefaultFilters": {
        "filter" => "myPrimaryFilter"
    }
}
```
    
## menu

Top-right menu for views (list, detail, edit). Available types: *buttons*, *dropdown*.

Example:

```json
{
    "menu": {
        "detail": {
            "buttons": [
                {
                    "labelTranslation": "Campaign.links.trackingUrls",
                    "link": "#CampaignTrackingUrl",
                    "acl": "read",
                    "aclScope": "CampaignTrackingUrl"
                }
            ],
            "dropdown": [
                {
                    "label": "Some Action",
                    "acl": "edit",
                    "aclScope": "SomeScope",
                    "action": "someAction"
                }
            ]
        }
    }
}
```

See [more](../custom-buttons.md).

## sidePanels

Definitions of side-panels for views (detail, edit, detailSmall, editSmall). Defined panels will be available in the layout manager.

Example: 

```json
{
    "sidePanels": {
        "detail": [
            {
                "name": "attendees",
                "label": "Attendees",
                "view": "crm:views/meeting/record/panels/attendees",
                "options": {
                    "fieldList": [
                        "users",
                        "contacts",
                        "leads"
                    ]
                },
                "isForm": true,
                "notRefreshable": true
            }
        ]
    }
}
```

### isForm

*boolean*

Needed for a proper UI styling when the panel contains a form.

### notRefreshable

*boolean*

Not refreshable (when clicking on the header).

### options

*string[]*

Options to pass to the panel view.
      
## bottomPanels

Definitions of bottom-panels for views. The same as sidePanels.

## relationshipPanels

Parameters to be applied for specific relationship panels.

Example:

```json
{
    "relationshipPanels": {
        "linkName": {
            "view": "my-module:views/panels/panel-view",
            "recordListView": "my-module:views/record/list",
            "rowActionsView": "my-module:views/record/row-actions/view",
            "label": "Panel Label",
            "readOnly": false,
            "selectDisabled": false,
            "createDisabled": false,
            "viewDisabled": false,
            "unlinkDisabled": false,
            "orderBy": "someField",
            "orderDirection": "asc",
            "createRequiredAccess": "read",
            "selectRequiredAccess": "edit",
            "selectPrimaryFilterName": "filterName",
            "boolFilterList": ["onlyMy"],
            "layout": "listLayoutName"
        }
    }
}
```

### layout

A layout name or a layout defined as an array.

### createDisabled

*boolean*

Disable the ability to create related records.

### selectDisabled

*boolean*

Disable the ability to select related records.

### viewDisabled

*boolean*

Disable the ability to view related records in a modal.

### unlinkDisabled

*boolean*

Disable the ability to unlink related records.

### label

*string*

A custom translatable label.

### createRequiredAccess

*string*

Access (to a current entity type) required for creating related records.

### selectRequiredAccess

*string*

Access (to a current entity type) required for selecting related records.

### filters

*string[]*

Filters available in the dropdown.

### orderDirection

*string*

`"asc"` or `"desc"`.

## additionalLayouts

Additionals layouts for a scope.

```json
{
    "additionalLayouts": {
        "detailConvert": {
            "type": "detail"
        },
        "listForAccount": {
            "type": "listSmall"
        },
        "listForContact": {
            "type": "listSmall"
        }
    }
}
```
    
## massActionList

*string[]*

Mass actions.

## checkAllResultMassActionList

*string[]*

Mass actions available when selecting all results.

## massActionDefs

*Object.<string, mixed\>*

Defenitions for mass actions.

### handler

*string*

A handler class for the mass action.

### initFunction

*string*

An init function of the handler.

### configCheck

*?string*

A config path (separated by the `.`) to check whether the action is enabled. The `!` prefix reverts.

### aclScope

*?string*

A scope access to which is required for the action.

### acl

*?string*

An acl action access to which is required for the action.

## detailActionList

*Object[]*

Detail view actions (available from the dropdown next to the *Edit* button).

### name

*string*

An action name.

### label

A translatable label.

### handler

*string*

A handler class for the action.

### initFunction

*string*

An init function of the handler.

### checkVisibilityFunction

*?string*

The handler function that checks whether the action is available. Should return a boolean value. Called on model sync.

### configCheck

*?string*

A config path (separated by the `.`) to check whether the action is enabled. The `!` prefix reverts.

### aclScope

*?string*

A scope access to which is required for the action.

### acl

*?string*

An acl action access to which is required for the action.

## modalDetailActionList

*Object[]*

Modal detail view actions. Parameters are the same as for *detailActionList*.

## iconClass

A scope icon class.

Example: `"fas fa-chess-king"`

## color

Scope color in HEX.

## kanbanViewMode

*boolean*

Whether the scope has the kanban view mode on the list view.

## allowInternalNotes

*boolean*

If true, it will be possible to post internal posts in the stream. Internal posts are not visible in portals.

## isExpandedByDefault

*boolean*

Actual for category scopes (e.g. DocumentFolder). If true, then by default it will be in expanded mode.

## dynamicLogic

[Dynamic logic](../../administration/dynamic-logic.md) definitions making a form dynamic.

```json
{
    "dynamicLogic": {
        "fields": {
            "fieldName": {
                "visible": {
                    "conditionGroup": []
                },
                "required": {
                    "conditionGroup": []
                },
                "readOnly": {
                    "conditionGroup": []
                }
            }
        },
        "panels": {
            "panelName": {
                "visible": {
                    "conditionGroup": []
                }
            }
        }
    }
}
```
