# Custom Events

- That we can use using Output Property.
- This is one Decorater and should inported from @angular/core.

    ```
        import {Component, Input, Output} from '@angular/core'

        @Output() <variableName> = 
    ```
- Unlike input, output property will recive an inicial value which assign with the equal sign.
- That is EventEmitter() objet which is also imported from @angula/core.
    ```
        import {Component, Input, Output, EventEmitter} from '@angular/core'

        @Input({required: true}) id!:string;
        // @Output() <variableName> = new EventEmitter<type>();
        @Output() select = new EventEmitter<string>();
        onSelectUser() {
            this.select.emit(this.id);
        }
    ```

    ```
    html
        <app-user [id]="users[0].id" [avatar]="users[0].avatar" [name]="users[0].name" (select)="onSelectUser($event)" />
    ts
         onSelectUser(_id:string) {
      console.log(`Selected user with id: ${_id}`);
      // You can add more logic here, like    navigating to a user detail page or    displaying more information.
    }
    ```
- We are passing $event in select binding.
- This is reserved name.
- This $event variable is not just available when working with custom events! It can also be used on build in events(like click) to get hold of potentially emiitted values.
- This $event will hold the data/value that was emmitted by the event we are lissining too.

# Uses of output() Function
- This is morden way to output the data 
- We should inport output function from the @angular/core

```
    import {output} from '@angular/core';

    select = output<string>();
```

- If we use output function, in that case we no neet to import EventEmitter.
- We can emit the event without EventEmitter.
```
onSelectUser() {
    this.select.emit(this.id());
}
```
- Here the emitted type we should specify while declaring.
- This is the replacement of @Output decorator.
- It will work same as @Output.
- output function will not create any type of signal. It is still eventEmitter.

## Extra info to EventEmitter
- We should pass emitted value type while declaring eventEmitter for typesefty.
```
     // @Output() <variableName> = new EventEmitter<type>();
        @Output() select = new EventEmitter<string>();
```
