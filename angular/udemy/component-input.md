# Component Input
- It is used to take data from outer container.
- We should import Input from angular/core.
- Add using Input decorator
    ```
        import { Component, Input } from '@angular/core';

        @Input() avatar!: string;
        @Input() name!: string;
    ```

- avatar and name is properties which we will bind while calling component

    ```
        <app-user [avatar]="users[0].avatar" [name]="users[0].name" />
    ```

## Required Input

- If input is required and we are not assigning the value while calling component, it will throw the error.

    ```
        import { Component, Input } from '@angular/core';

        @Input({
            required: true
        }) avatar!: string;
        @Input({
            required: true
        }) name!: string;
    ```

## Signal Inputs

- Import input with lower case i from @angular/core.
- Upper case it is Decorator.
- Lower case it is special function.
    ```
        import { Component, input } from '@angular/core';

        avatar = input<type of value | string>('<Default value>');
    ```
- Required input
    ```
        import { Component, input, computed } from '@angular/core';

        avatar = input.required<string>();
        name = input.required<string>();

        imagePath = computed(()=>{
          return `assets/users/${this.avatar()}`;
        })
    ```
- If it is required, we can not pass inicial value.
- Out side of the coponent, it doesn't matter like the input is decorator or signal.
- In Signal we don't want ! as we required on top.
- While using signal input in tempate we use () as well to get the value.

    ```
        <div>
            <button (click)="onSelectUser()">
                 <img [src]="imagePath()" [alt]="name()" />
                <p>{{name()}}</p>
            </button>
        </div>
    ```
- We can not update the signal input value from the component.

## Which input should use

- Decorator based @Input or signal based input().
- Signal based inputs are more efficent then decorator based.
- Signal based inputs are newly introduses. 
- If efficency is not required, we can use anyone.
