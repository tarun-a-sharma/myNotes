# Type Script

## Required and Undefined values and Union Type

- Form optional we use ? and for required we use !
```
@Input name!:string;
@Input selectedUser?:string;
```

- ? is JS syntext, which tells if value is there use that or else undefind.
```
<app-tasks [name]="selectedUser ? selectedUser.name : ''">
```

## Alternative Syntext of ?

- We can change type to either and or way
```
@Input selectedUser:string | undefined;
``` 
- | is create union types.

## Object as Inputs

- We can pass like this 
```
user = input.required<{id: string, avatar: string, name: string}>();
```

## Type Aliases
- To create type aliase, we can use type keyword after that any name which we want.
- Name should starts with Uppercare char.
```
type <Name>

type User = {
    id: string;
    avatar: string; 
    name: string;
}


user = input.required<User>();
```

## Interfaces
- We have another way to defining object type
- For that we can use interface keyword and after that name which we want.
- Here we are not adding = sign as type.
```
inetrface <Name>

inetrface User{
    id: string;
    avatar: string; 
    name: string;
}


user = input.required<User>();
```
- User interface we can defind only object type but using interface we can defind other types as well.

