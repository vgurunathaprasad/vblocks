# Visual Stack - Data Model

## Basic Classification of interactive objects

- Data Block
  - Simple Input Loader
  - Special Input Loader
  - File Stream Input Loader
- Functional Block
  - Builtin Function Block
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
            "pre-requisites" : []
        },
        
    }
}
```

Every sheet created is covered with `game-plan` class. Inside `game-plan`, the sequence of the program is drawn. FYI unit of code in a visual interface will be called **block**. Every block will contain three elements by default, `"block_id"`, `"block_type"`, `"pre-requsites"`. Each block in the code area will be indentified by a unique **block_id". The **block_type** says what type of block it is (Block Type will be a unique string value representing the different types of blocks listed above). **pre-requsites** is an array block that contains the list of blocks intercepted before handling the current block.

Few JSON samples of the blocks listed above are as follows....

## Simple Input Loader Block

Simple Input Loader Block will be used to provide a single data input to a function. The respective block's JSON reflection is given below.

```
{
    "game-plan" {
        "block_1"{
            "block_id": "0x12fcea",
            "block_type": "simple_input",
            "input" : {
                "data": "",
            },
            "pre-requsites" : []
        }
    }   
}
```

## Special Input Loader Block

Special Input Loader Block is used to provide special or collective inputs to a function block. The respective block sample JSON reflection is as follows...

```
{
    "game-plan" : {
        "block_1":{
            "block_id": "0x12fcea",
            "block_type": "special_input",
            "inputs" : [
            {}, 
            {}, 
            {} ],  // multiple input elements
            "pre-requisites" : []
        }
    }
}
```

## File Stream Input Loader Block

File Stream Input Loader Block  as the name suggests will be used to load files and use then as an input to a function. It must be understood that this block after selction of the file, the file will be uploaded to the server and respective file's URL will be appended with the block. On function call the provided URL will be processed to get the file.

```
{
    "game-plan" : {
        "block_1":{
            "block_id": "0x12fcea",
            "block_type": "file_input",
            "input" : {
                "file_url": "https://uploaded.url/filename.ext",
                "file_type" : "csv"
            },
        "pre-requisites" : []
        }
    }
}
```
## Builtin Function Block

A Built in Function Block will be pre-listed and will represent a pre-implemented function on the server side. The below provided will represent a Built in Function block...

```
{
    "game-plan" : {
        "block_1":{
            "block_id": "0x12fcea",
            "block_type": "buildin_function",
            "function":{
                "function_name": "function1",
            },
            "pre-requisites" : []
        }
    }
}
```

## Custom Function Block

The Custom Function Block will allow the user to create user defined module or script on the server side and will allow the user to use the same in the play book. On creation if a Custom Function Block, a script file will be created in the server side and user's script will be written to the same. The JSON representation will use URL to locate the script and refer it when required while running the play book.

```
{
    "game-plan" : {
        "block_1":{
            "block_id": "0x12fcea",
            "block_type": "custom_function",
            "function": {
                "payload_url": "https://uploaded.url/payload",
                "function_name": "function1",
                "payload_prerequsites": []
            },
            "pre-requisites" : []
        }
    }
}
```

## Special Function Block

Special Function block will allow the user to combine more than one functional block, so that it can be ran at one shot.

```
{
    "game-plan" : {
        "block_1":{
            "block_id": "0x12fcea",
            "block_type": "special_function",
            "functions": [ {}, {} , {} ],
            "pre-requisites" : []
        }
    }
}
```

## Binary Conditional Block

A Binary Conditional Block will allow the control flow of the play book to switch blocks based on a condition based on a Binary result switch (True or False condition).

```
{
    "game-plan" : {
        "block_1":{
            "block_id": "0x12fcea",
            "block_type": "conditional_binary",
            "condition" : {
                "lhs_block": "lhs_block_id",
                "rhs_block": "rhs_block_id",
                "conditinal_operation": "CONDITIONAL_OPERATOR",
                "on_pass": "block_id",
                "on_fail": "block_id"
            },
            "pre-requisites" : ["lhs_block":{}, "rhs_block": {}, "on_pass_blk": {}, "on_fail_blk":{} ]
        }
    }
}
```

## Fuzzy Conditional Block

Fuzzy Conditional Block is used whem the condition may end up suggesting more than two paths. In other words it is a way to have multiple conditional flow in your play book.

```
{
    "game-plan" : {
        "block_1":{
            "block_id": "0x12fcea",
            "block_type": "conditional_fuzzy",
            
            "condition_1" : {
                "lhs_block_1": "lhs_block_id",
                "rhs_block_1": "rhs_block_id",
                "conditinal_operation": "CONDITIONAL_OPERATOR",
                "on_pass_1": "block_id",
                "on_fail_1": "block_id"
            },

            "condition_2" : {
                "lhs_block_2": "lhs_block_id",
                "rhs_block_2": "rhs_block_id",
                "conditinal_operation": "CONDITIONAL_OPERATOR",
                "on_pass_2": "block_id",
                "on_fail_2": "block_id"
            },

            "condition_3" : {
                "lhs_block_3": "lhs_block_id",
                "rhs_block_3": "rhs_block_id",
                "conditinal_operation": "CONDITIONAL_OPERATOR",
                "on_pass_3": "block_id",
                "on_fail_3": "block_id"
            },
            "pre-requisites" : ["lhs_block_1":{}, "rhs_block_1": {}, "on_pass_blk_1": {}, "on_fail_blk_1":{},
                                "lhs_block_2":{}, "rhs_block_2": {}, "on_pass_blk_2": {}, "on_fail_blk_2":{},
                                "lhs_block_3":{}, "rhs_block_3": {}, "on_pass_blk_3": {}, "on_fail_blk_3":{} ]
        }
    }
}
```





