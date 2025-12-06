# Style

## Class Binding 

- We can bind class with . and class name that will be equal to condition
- [class.<className>] = "<condition>"
```
 <button (click)="onSelectUser()" [class.active]="selected()">
     <!-- <img src="assets/users/{{selectedUser.avatar}}" /> -->
      <!-- <img [src]="'assets/users/' + selectedUser.avatar" [alt]="selectedUser.name" /> -->
      <img [src]="imagePath()" [alt]="user().name" />
     <p>{{user().name}}</p>
 </button>
```

- Here I want to add class active to selected user
