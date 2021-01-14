# Visual Stack - Data Model

## Basic Classification of interactive objects

- Data Block
  - Simple Input Loader
  - Special Input Loader
  - File Stream Input Loader
- Functional Block
  - Builtin Functional Block
  - Custom Function Block
  - Special Function Block
- Conditional Block
  - Binary Conditional Block
  - Fuzzy Conditional Block
- Output Block
  - Default Output Block
  - Custom Output Block
  - Visual Output Block
  - Action Output Block
 
All the blocks specified above are considered nestable and interoperable.

## Data Model - JSON Representation

### Basic Template of any Block

```
{
    "game-plan" : {
        "block_1":{
            "block_id": "0x12fcea",
            "block_type": ""
        },
        "pre-requisites" : []
    }
}
```


