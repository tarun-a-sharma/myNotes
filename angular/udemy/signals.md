# Signals

- Requires usage of sepcial "signal" instuctions & code.
- Supported since Angular 16
- A signal is an object that stores a value (any type of value, including nested objects)
- Angular manages subscriptions to the signal to get notified about value changes.
- When a change occures, Angular is then able to update the part of the UI that needs updating.
- Import : 
    ```
        import { signal } from '@angular/core';
    ```
- Inicialize signal: Add signal keyword in variable and add the value in ()
    ```
        selectedUser = signal(DUMMY_USERS[randomIndex])
    ```

- Update Signal: Add set and give the updated value in ()
    ```
        const randomIndex = Math.floor(Math.random() * DUMMY_USERS.length);
        this.selectedUser.set(DUMMY_USERS[randomIndex]);
    ```
- Deleing with signals: ecexute signal while using.

    ```
        <div>
            <button (click)="onSelectUser()">
                 <img [src]="imagePath" [alt]="selectedUser().name" />
                <p>{{selectedUser().name}}</p>
            </button>
        </div>
    ```
- Without signals we use computed value using getter, get function.
- Using signal, computed value using adding other regular property and then we can use computed function which is also imported from @angular/core.
- Computed will work with signals
- Computed will take a function as an aregument.
    ```
        import { Component,computed ,signal } from '@angular/core';


        export class User {
          selectedUser = signal(DUMMY_USERS[randomIndex]);
          imagePath = computed (()=>{`assets/users/${this.      selectedUser().avatar}`;}) 

          // get imagePath() {
          //   return `assets/users/${this.selectedUser.avatar}     `;
          // }

          onSelectUser() {
            const randomIndex = Math.floor(Math.random() *      DUMMY_USERS.length);
            this.selectedUser.set(DUMMY_USERS[randomIndex]);
          }
        }
    ```
- Computed property should be executed because at the end that is also a signal.
    ```
        img [src]="imagePath()" [alt]="selectedUser().name" />
    ```
- Using .asReadOnly() with signal we can make that as non ediatable, that is alternative of computed thing. 
- We can skip computed and use this.

    ```
        result = this.investment.resultData.asReadOnly();
    ```