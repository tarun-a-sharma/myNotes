# Condition

## If

- We can add condition in template using @if (condition)

```
@if(selectedName) {
    // template
} 

@if(selectedName) {
    <app-tasks [name]="selectedName" />
}
```

- We can write @else also for fallback

```
@if(selectedName) {
    <app-tasks [name]="selectedName" />
} @else {
    <h2>Select a user to see tasks</h2>
}
```

- We can also add "else if(condition)" bloacks if we wanted to check for alternative condition.

```
@if (condition1) {
  <div>Condition 1 is true</div>
} @else if (condition2) {
  <div>Condition 2 is true</div>
} @else {
  <div>No condition is true</div>
}
```


## Old Syntax

- First we need to import NgFor from @angula/common.
- Add that in import array.

```
    app.ts

    import {NgIf} from '@angular/common'

    @Component({
         selector: 'app-root',
         imports: [HeaderComponent, User, Tasks, NgIf],
         templateUrl: './app.html',
         styleUrl: './app.css'
    })
```

- Then we can use in component template

```
    <app-tasks *ngIf="selectedUser; else fallback" [name]="selectedUser!.name" />
    <ng-template #fallback>
        <p>Select User to drr their tasks!</p>
    </ng-template>
```

- Here we need to add *ngIf to the element where we want to add contition.
- After condition we can write else contion also but that else thing is a bit complex.
- First we need to create a fallback template using <ng-template>, which is specially angular template styling and add #<any-id>, that Id we will add in else condition.
