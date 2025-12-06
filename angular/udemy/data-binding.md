# Outputting Dynamic Content
- There are two yas to outputting data, one is String Interpolation and other is property binding.
- String Interpolation: two opening {{ and colsing }} and inside that any public property on component class.
    ```
    <span>{{ selectedUser.NAME }}</span>
    ```
- Property Binding: opening [ and closing ] around the property name.
    ```
        <img [src]="'assets/users/' + selectedUser.avatar" [alt]="selectedUser.name" />
    ```

- Since "Property Binding" wants to target properties (and not attributes), that can be a problem. That's why Angular offers a slight variation of the "Property Binding" syntax that does allow you to bind attributes to dynamic values.
- It looks like this:
    ```
        <div 
        role="progressbar" 
        [attr.aria-valuenow]="currentVal" 
        [attr.aria-valuemax]="maxVal">...</div>
    ```

- By adding attr in front of the attribute name you want to bind dynamically, you're "telling" Angular that it shouldn't try to find a property with the specified name but instead bind the respective attribute - in the example above, the aria-valuenow and aria-valuemax attributes would be bound dynamically.
- If we want to assign string value in property binding, we can skip [].

# Getters for Computed Values
- Using getter function we no need to executer that funtion to get the value.
    ```
        export class User {
            selectedUser = DUMMY_USERS[randomIndex];

            get imagePath() {
              return `assets/users/${this.selectedUser  avatar}`;
            }
        }

         <img [src]="imagePath" [alt]="selectedUser.name" />
    ```

# Events

- Add events in angular, we wrap event name in ().
    ```
        <button (click)="onSelectUser()" >Submit</button>

        export class UserComponent {
            onSelectUser() {
                console.log('Clicked!')
            }
        }
    ```

# Form Submit event 

- Add (ngSubmit) in the form tag.

# Managing State and Changing Data
- Update variable in ts file, data will update in design as well.

```
    export class User {
      selectedUser = DUMMY_USERS[randomIndex];

      get imagePath() {
        return `assets/users/${this.selectedUser.avatar}`;
      }

      onSelectUser() {
        const randomIndex = Math.floor(Math.random() *  DUMMY_USERS.length);
        this.selectedUser = DUMMY_USERS[randomIndex];
      }
    }
```
- Angular is ahndling state using zone.js