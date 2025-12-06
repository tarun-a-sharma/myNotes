# Pipes
- Output transformers, things that transform the output in templets.
- We can import pipes DatePipe from @angular/common.
- We can create our own Pipes
- More Pipes we can check in Angular documentation [Pipes](https://angular.dev/guide/templates/pipes)

```
ts

import { DatePipe } from '@angular/common';

@Component({
  selector: 'app-task',
  imports: [Card,DatePipe],
  templateUrl: './task.html',
  styleUrl: './task.css'
})

html
 <time>{{task().dueDate | date:'fullDate' }}</time>
```

- We can specify the angular pipes as well after adding : 