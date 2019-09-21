
# Permission Documentation

  Permission documantation by examples, encodes and CHMOD system. Permission algorithm works from top to bottom !

## Example Data as JSON 
```js
[
  {
    "code": "permission.internal-control",
    "name": "internal-control",
    "pages": [
      {
        "code": "permission.internal-control.details",
        "name": "details-page",
        "components": [
          {
            "code": "permission.system.internal-control.details.costs",
            "name": "costs",
            "component-items": [
              {
                "code": "permission.system.internal-control.details.costs.delete_button",
                "name": "delete_button",
                "permissions": [
                  {
                    "code": "permission.internalControl.project.costs.delete_button.0",
                    "name": "NO_PERMISSION"
                  }
                ]
              }
            ]
          }
        ]
      }
    ]
  }
]
```
## ENCODE: 

```js
permission.${module}.${page}.${component}.${component_id}${permission}
```

### Example ENCODEs: 

```js
**No Permission:** permission.internal-control.project.*.*.NO_PERMISSION(0)
**Read ALL:** permission.internal-control.project.*.*.READ(1)
**ALL:** permission.internal-control.project.*.*.ALL(7)
**All Buttons Example**: permission.internal-control.project.*.*.no_permission
permission.internal-control.project.create
```

### Example ENCODE with Advanced Use Case: 

```js
(Buro) permissions: [
    "permission.internalControl.project.*.*.READ",
    "permission.internalControl.project.*.ihaneAdi.7",
    "permission.internalControl.project.*.biddingNo.0",
    "permission.internalControl.project.button.*.7",
    "permission.internalControl.project.costs.*.0",
    "permission.internalControl.project.dates.*.0",
]
```

## Fundamental CHMOD Architecture
| Value | R   | W   | X   | Description   |
| ----- | --- | --- | --- | ------------- |
| 0     | 0   | 0   | 0   | NO_PERMISSION |
| 1     | 1   | 0   | 0   | READ          |
| 2     | 0   | 1   | 0   | WRITE         |
| 3     | 1   | 1   | 0   | READ/WRITE    |
| 4     | 0   | 0   | 1   | EXECUTE       |
| 5     | 1   | 0   | 1   | READ/EXECUTE  |
| 6     | 0   | 1   | 1   | WRITE/EXECUTE |
| 7     | 1   | 1   | 1   | ALL           |
