# Directives

- Components are directives, Directives without templates.
- Directives are not having templates.

# Two Way Binding 

- ngModel directive used for two way binding.
- Two way binding is not be used on any property of element. By default no element property supported. 
- We have to register ngModel directive. 
- For that we have to import FormsModule from @angular/forms
- FormsModule is collection of directives

```
import { FormsModule } from '@angular/forms';

@Component({
  selector: 'app-new-task',
  imports: [FormsModule],
  templateUrl: './new-task.html',
  styleUrl: './new-task.css'
})

export class NewTask {
  cancel = output<void>();
  enteredTitle = '';
  onCancel() {
    this.cancel.emit();
  }
}

 <input type="text" id="title" name="title" [(ngModel)]="enteredTitle" />
```

# Signals & Two-way-binding
- In template side it will be the same but in .ts file we should assign variables as signals.
- Even no need to add () in templates as well.
```

enteredTitle = signal('');
enteredSummary = signal('');
enteredDueDate= signal('');

```


