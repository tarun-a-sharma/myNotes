# For

- using @for we can loop

```
    @for (<variable-name> of <array-which-we-want-to-loop>; track <any-identifier> ) {
        // looping design
    }

    @for (user of users; track user.id) {
        <li>
            <app-user [user]="user" (select)="onSelectUser($event)" />
        </li>
    }
```

- Here we are looping users array and passing that instences to the component.
- We add track because we are dynamically outputting list data and angular internally wants to keep track items that is bing rendered.
- If any data will change, angular could easily reuse already rendered items and doen't have to recreate entire thing again and again.
- With the track expression here we are telling angular uniqe identification can be assign by angular behind the seens to every element it's rendering.

## Old Syntax
- First we need to import NgFor from @angula/common.
- Add that in import array.

```
    app.ts

    import {NgFor} from '@angular/common'

    @Component({
         selector: 'app-root',
         imports: [HeaderComponent, User, Tasks, NgFor],
         templateUrl: './app.html',
         styleUrl: './app.css'
    })
```

- Then we can use in component template

```
    <li *ngFor="let user of users">
        <app-user [user]="user" (select)="onSelectUser($event)" />
    </li>
```

- Here *ngFor is structural directive, structural directive is the enhancements which will change the element or change the DOM element.
