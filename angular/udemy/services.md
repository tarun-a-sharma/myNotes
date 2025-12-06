# Services

- We can start with creating a file
- Service is an other class
- We have to register this service/class with injectable angular. So that angular will know.
- To inject we should @Import decorater which is imported from @angular/core
- We can add it as execute as function and then we can pass config obj to it.

```
@Injectable({providedIn: 'root'})
export class TaskService { 
    private  tasks = [
      {
        id: 't1',
        userId: 'u1',
        title: 'Master Angular',
        summary:
          'Learn all the basic and advanced features of Angular & how to apply them.',
        dueDate: '2025-12-31',
      },...
    ];

    getUserTasks(userId: string) {
        return this.tasks.filter(task => task.userId === userId);
    }

    addTask(taskData: NewTaskData, userId: string) {
        this.tasks.unshift({
            id: new Date().getTime().toString(),
            userId: userId,
            title: taskData.title,
            summary: taskData.summary,
            dueDate: taskData.dueDate
        });
    }
    
    removeTask(taskId: string) {
        this.tasks = this.tasks.filter(task => task.id !== taskId);
    }
}
```

- To use service in angular project, we can import service file.
```
import { TaskService } from './tasks.service';
```
- We can not directly work on TaskService, we have to make instent on that class using new
```
private service = new TaskService();
```
- But if we will do that and will use the same service in many component, data will not update accordingly.
- Because we created the new instence of the service.
- To overcome that issue, angular introduse Dependency Injection.
- In the caller component, we can add that in constructor's argument
```
private taskService: TaskService
constructor(taskService: TaskService){
    this.taskService = taskService;
}

OR

constructor(private taskService: TaskService){}

```

- We can inject using, inject which is import from @angula/core
```
import { inject } from '@angular/core';

 private taskService = inject(TaskService);

 onSubmit() {
    this.taskService.addTask({
      title: this.enteredTitle,
      summary: this.enteredSummary,
      dueDate: this.enteredDueDate
    }, this.userId());
    this.enteredTitle = '';
    this.enteredSummary = '';
    this.enteredDueDate = '';
  }
```
- This is simply an alternative of @Injectable decorator