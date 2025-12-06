# Create Component

- File name should be component-name.component.ts
- As per Angular 20+, filename convention can be
  - app.css
  - app.html
  - app.ts
  - header.ts
  - etc...
- Let say we are creating header as component, in that case header.component.ts
- In header.component.ts file
  ```
  import { Component } from '@angular/core';
  @Component ({
      selector: 'app-header',
      template: '',
      standalone: true,
      templateUrl: './header.component.html',
      styleUrl: '',   //If having one stylesheet
      styleUrls: [],   // If having multiple stylesheets
      styles: ['h1 {color:red}']  // This is inline styling
  })
  export class HeaderComponent {}
  ```
- Import component from angular.
- Here @Component is a decorator which is holding metadata and configuration classes.
- Decorator is a TS concept.
- Classes are the blueprint of object.
- Selector is the name of out component.
- It will be good if we can give atleast 2 words name. Because if it is one word in that case it might be override any existing default name.
- If Angular version is heigher or equal to 19, this is true by default. Or else we can make it true here.
- If it is false, component is treated as module based component.
- template is defind for a markup of the component. This is online markup.
- templateUrl contains the string of relative path of component markup design.

# Use component

- In main.ts file, import header component and add the below things

  ```
  import { bootstrapApplication } from '@angular/platform-browser';
  import { AppComponent } from './app/app.component';
  import { HeaderComponent } from './app/header.component';

  bootstrapApplication(AppComponent).catch((err) => console.error(err));
  bootstrapApplication(HeaderComponent).catch((err) => console.error(err));
  ```

- import without .ts
- This approch is not recommendded. Because angular follow tree based arch.
  \_ Normally our main component is App component. So what will we do,.. we import herder component in app.component.ts file and registered with imports in Component decorator something like this

  ````
  import { Component } from '@angular/core';

      import { HeaderComponent } from '.header.component';

      @Component({
          selector: 'app-root',
          standalone: true,
          imports:[HeaderComponent],
          templateURL: './app.component.html',
          styleUrl: './app-component.css,
      })

      export class AppComponent {}

      ```
  ````

# Styling the component

- Add styleUrls in @Component decoretor.
- That will be array of all the style files.

  ```
      @Component({
          selector: 'app-root',
          templateURL: './app.component.html',
          styleUrls: ['./app-component.css', 'style2.css'],
      })
  ```

- If we have single file in that case we can use styleUrl.

  ```
      @Component({
          selector: 'app-root',
          templateURL: './app.component.html',
          styleUrl: './app-component.css',
      })
  ```

- We can add just styles property which will be the array of inline styles

  ```
      @Component({
          selector: 'app-root',
          standalone: true,
          imports:[HeaderComponent],
          templateURL: './app.component.html',
          styles: ['h1 {color: red}'],
      })
  ```

# Add Assets folder

- In angular.js, add folder path in "assets" key
  ```
      "assets":[
          "src/assets"
      ]
  ```
- Then we can use assets directly, without relative path.

# Manage and creating components with the Angular CLI

- To generate components using CLI

  ```
      ng generate component path/<component-name>
  ```

  OR

  ```
      ng g c path/<component-name>
  ```

# Storing Data

- We can store data in side the class.

  ```
      @Component({
        selector: 'app-user',
        imports: [],
        templateUrl: './user.html',
        styleUrl: './user.css'
      })

      export class User {
        selectedUser = DUMMY_USERS[randomIndex]
      }
  ```

- We can use selectedUser inside the template file.

# Dynamic design in Component

- If we want to wrap other design in component, we can use <ng-content /> in the component where we want to load design.

```
<div>
    <ng-content />
</div>

```

- We can impoer that component and use

```
ts

import { Card } from "../../shared/card/card";

@Component({
  selector: 'app-user',
  imports: [Card],
  templateUrl: './user.html',
  styleUrl: './user.css'
})

html

<app-card>
    <button (click)="onSelectUser()" [class.active]="selected()">
         <img [src]="imagePath()" [alt]="user().name" />
        <p>{{user().name}}</p>
    </button>
</app-card>
```

# Multiple Slots

- We can use select attribute with <ng-content />
```
    <span> 
        <ng-content />
    </span>
    <ng-content select="<selector>" />

    <span> 
        <ng-content />
    </span>
    <ng-content select=".icon" />
```
- Here .icon is selector which we can use to show out content in 2nd ng-content 
```
<button appButton>
  Logout
  <span class="icon">→</span>
</button>
```
- Here Logout is for first ng-content.
- As selector we gave as icon in 2nd ng-content, that's why we added icon as class in span or any other tag.

# Advanced Content Projection

- As above it is not as use full as we want because if I added some css in component, I should follow the same tag to get that styling.
- If I add, that tag in component in that case nested and tag duplication will occure in DOM.
- To prevent that issue we can use selector without any css selector.
- We can bind that in parent component with ngProjectAs.

```
<span>
  <ng-content />
</span>
<span class="icon">
  <ng-content select="icon" />
</span>


<button appButton>
  Submit
  <i ngProjectAs="icon">⌲</i>
</button>
```

# Content Projection Fallbacks
- We can add any default value for the ng-content.
```
button.component

<span>
  <ng-content />
</span>
<span class="icon">
  <ng-content select="icon">→</ng-content>
</span>


comp1.component
<button appButton>
  Logout
</button>

comp2.component
<button appButton>
  Submit
  <span ngProjectAs="icon">⌲</span>
</button>
```
- We can use multiple select in ng-content with coma seprated.
```
<p>
  <label>{{label()}}</label>
  <ng-content select="input, textarea" />
</p>
```
- We can use multiple component selector as well with comma seprated 



# Custom Components via Attribute Selectors

- As above stye if we create any component, it will wrap out content in one parent component.
- To prevent that, we can use Attribut Selector.
- It will be the same as bove but the selector name in COmponent directive, we will write arrtibute name using []. Angular will treated as attribut component.

```
    ts

    import { Component } from '@angular/core';

    @Component({
      selector: 'button[appButton]',
      standalone: true,
      imports: [],
      templateUrl: './button.component.html',
      styleUrl: './button.component.css'
    })
    export class ButtonComponent {

    }

    html

    <button appButton></button>


```

# Scoping CSS Style
- In Style.css is global css style sheet.
- For component styles, we can add in component.css file.
- It will restricted in component, it will not impect other page css.
- Angular will just care about what selector item in the component not the nested things.
- To working, we can disable the scoping in the component.
- For that we can add in @Component encapsulation: ViewEncapsulation
- Default value is 
```
ViewEncapsulation.Emulated : 
```
