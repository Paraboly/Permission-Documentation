
# Permission Documentation

  Permission documantation by examples, encodes and CHMOD system.
  
 ### **One and Only Important Note:** 
 Permission algorithm works from top to bottom !

## Example Data as JSON 
```js
[
  {
    "code": "permission.system",
    "name": "system",
    "pages": [
      {
        "code": "permission.system.details",
        "name": "details-page",
        "components": [
          {
            "code": "permission.system.system.details.costs",
            "name": "costs",
            "component-items": [
              {
                "code": "permission.system.system.details.costs.delete_button",
                "name": "delete_button",
                "permissions": [
                  {
                    "code": "permission.system.project.costs.delete_button.0",
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


**No Permission:** ```permission.system.project.*.*.NO_PERMISSION(0)```
</br>
**Read:** ```permission.system.project.*.*.READ(1)```
</br>
**ALL:** ```permission.system.project.*.*.ALL(7)```
</br>
**All Buttons Example**: ```permission.system.project.*.button.NO_PERMISSION(0)```
</br>


### Example ENCODE with Advanced Use Case: 

```js
(Buro) permissions: [
    "permission.system.project.*.*.READ",
    "permission.system.project.*.price_tag.7",
    "permission.system.project.*.delete_button.0",
    "permission.system.project.button.*.7",
    "permission.system.project.costs.*.0",
    "permission.system.project.dates.*.0",
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
