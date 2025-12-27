# The What and Why of Signals

## What is Signal?

- Signal is a container that holds value.
![alt text](image.png)

![alt text](image-1.png)

![alt text](image-2.png)

![alt text](image-3.png)

## Why SIgnals?

![alt text](image-4.png)

![alt text](image-5.png)

![alt text](image-6.png)

![alt text](image-7.png)

![alt text](image-8.png)

- Without signal, Angular handels change detection with the help of zone.js
- But zone.js triggers too many updates, makes change detection slower, bloats our application.
- With Signals angular handles change detections without the zone.js

![alt text](image-9.png)

- Signals are a key part of many Angular features.
- And they are Reactive Primitive.

 ## What should be a Signal?

 - If a UI value can change, it should be a signal
 ![alt text](image-10.png)
 - If a value should react when another signal changes, it should be a signal.
![alt text](image-11.png)

## What, Why and Which of Signals

![alt text](image-12.png)

- Signals are synchronous
![alt text](image-13.png)

# Create and Reading Signals
## Signal Syntax

- Creat a signal using a signal constructor function.
- Optionally defind a type with a gereric peramiter, which is the type of the value stored in the signal.
- in side (), we add requird inicial value.
![alt text](image-14.png)
- We read a signal value using signal name and empty peranthisis
![alt text](image-15.png)

![alt text](image-16.png)

![alt text](image-17.png)

![alt text](image-18.png)

## Creating and Reading a Signal

- import signal from '@angular/core'
- declare variable in component class that will be equal to signal.
- signal required inicial value.
![alt text](image-19.png)

- We don't need to specify the type of data, it will take inicial value's type.

## Working with Arrays as Signals
- When working with lists of data, we often store that data in an array. To declare a signal that holds an array, we use the same signal constructor function syntax. First, the signal name.
- A signal always requires an initial value.

![alt text](image-20.png)

## Working with Object as Signals
- For object also we can declare the signal as same way like signal constructor function syntax.
- If the signal is object, we need to tell the interface of the object.
- If signal inicial value is undefind, we can use | in that 
- For eg.

![alt text](image-22.png)

![alt text](image-23.png)

- For safe navigation we use Safe Navigation Operator "?". This is also called as optional chain operator.

![alt text](image-21.png)

- Angular developers have been told not to call a function from a template. That's because of the way change detection currently runs for components and the possibility that the function could perform time‑consuming logic. 
- These concerns don't apply to signal getter functions. These functions are efficient getter accessors that do minimal work. Calling signal getters repeatedly and frequently is not an issue. 

![alt text](image-24.png)

## Changing a Signal's Value
- We can programatically store a new value in signal using set() and update().

### Using set()
- We can set the value in the signal as per our requirement.
![alt text](image-25.png)

### Using update()
- Update methods gives us the current signal value.
- And we provide the code using our existing value normally in the form of the arrow function.
![alt text](image-26.png)
- update() methods first parameter is the function who's attribute holds current signal value.
![alt text](image-27.png)

![alt text](image-28.png)
- Use the signal set method any time you want to set a specific value into a signal. 
- Use the signal update method to calculate a new value based on the current value.

## effect() and Debugging Tips
- Debugging signals, we use signal effect() feature.
- With the effect we run our code whenever signal change.
- effect() acceps a function as argument, it doen't need any values from the effect.
- We can write our code in that function.
![alt text](image-29.png)
- An effect() is scheduled to be run whenever any of its dependent signals change.
-  Unlike an observable, an effect doesn't immediately react to a notification. Rather, it waits for its turn to execute. 
- effect() waits till the method is not going to complete.
![alt text](image-30.png)
![alt text](image-31.png)
- In this case, qtyEffect will give o/p as 12.

## Debugging 
![alt text](image-32.png)
![alt text](image-33.png)

# computed() and linkedSignal()
- We can create reactive signal using computed() and linkedSignal()
## computed() Signal
- A computed() signal performs a computation whenever dependent signals change. 
- computed should be import from @angular/core
- It react to the change automatically re calculate the value.
- Create a computed signal using a computed constructor function. Passing a arrow function without any arguments.
- computed signal will be read only not writable.
![alt text](image-34.png)
- Nullish coalescing operator.
![alt text](image-35.png)
- This operator says if the left side is null or undefind, we use the default value in the right insets.
- Use a computed() signal to perform a calulation, modify the UI or execute a compitation any time one and more dependant signal changed.
- computed() is read only.

## linkedSignal()

- A linkedSignal() creates a writable signal that automatiaclly resets when dependent signals change.
![alt text](image-36.png)

![alt text](image-37.png)

![alt text](image-38.png)

![alt text](image-39.png)

![alt text](image-40.png)

![alt text](image-41.png)

![alt text](image-42.png)

## computed() vs linkedSignal()

![alt text](image-43.png)

# Retrieving Data into a Signal

## Observale vs httpResource()

![alt text](image-44.png)

![alt text](image-45.png)

![alt text](image-46.png)

![alt text](image-47.png)

![alt text](image-48.png)

## Retrieving Data into a Signal with httpResource()

- httpResource() uses httpClient. httpClient is an angular's library for performing http request.
- We do that in the app.config.ts file -> providers 

![alt text](image-49.png)

- Best practice to retrive http data from the service.
- For example we need product data from server, we create product service and in that we declare the product API endpoint.

![alt text](image-50.png)

- To retrive data from the endpoint, we start by creating a resource.
- Declare the variable and thenm call httpResource().
- To strongly type the return data, specify a generic argument.
- HttpResource requires passing in a function. That function returns the URL for the HTTP endpoint. 
- Recall that a signal must always have a value. So when a resource is first created, by default its value signal is undefined,
- If we don't want the handle undefined everywhere, use the options parameter of the resource function to provide a default value. The options parameter is an object, so we add curly braces, set the defaultValue property of the object to an empty array. 

![alt text](image-51.png)

- Handle default value of the hpptResource
![alt text](image-52.png)

- When does this httpRequest execute? When this service is initialized, all of its variables are declared. When the resource is declared, it immediately executes and issues the HTTP request. 
- When the HTTP response is returned, the response data is set in the resource value signal. 
- That resource and its value signal remain until the service is destroyed. That way, we can share the value with any component or other services. 
 
![alt text](image-53.png)

- To acces the service, we need the instance of the service.
- We get that by injecting the service.
- To inject the service, we cerate the vatiable and write inject(). 
- Inside inject() function we pass the service class name which we want to inject.
- If this is the first time the service is injected in the application, the service is initialized. The inject method provides the instance to that service. 
- If the service is injected again, we get the original service instance. We use that instance variable to access our service. 
- Best practices suggest that we make our injected service private by adding the private keyword at the front. 
- The template should not access the service directly, but rather use the signals defined in our component.
- We declare the resource here in our service. We provide the URL and a default value. 
- In the component, we inject that service, then use the service instance to access the value property of the resource. That property will contain our retrieved data.
![alt text](image-54.png)

## Returning a Resource from a Method

- We define a function that returns the resource.
- In the function, return the same resource.
- This resource is now created when this function is called, not when the product service is initialized. We'll call this function in the component. Declare a variable. 
![alt text](image-55.png)

## Resource Properties: isLoading and Error

- When accessing data, two features we often need are a loading indicator and error handling. 
- Angular's Resource API helps us with both. Looking at the Product Selection component, we access the retrieved products using the resource value signal. If I place the cursor after the last dot and press Ctrl + Space, I get a list of the features that the resource provides. It includes error, isLoading, status, and value. 

![alt text](image-56.png)

![alt text](image-57.png)

![alt text](image-58.png)

## Common Resource API Questions

![alt text](image-59.png)

### Where should we declare our Resources?

![alt text](image-60.png)

### Can I still use my interceptors? 
-Interceptors are a form of middleware. They are functions that run either before an HTTP request is sent to the server or after the response is returned. And yes, since httpResource uses httpClient, you can still use interceptors as needed. 

![alt text](image-61.png)

### Can we use the Resource API for mutation operations such as an update?
- Nope, the Angular team does not recommend using the Resource API for update operations. It's only meant for retrieving data. That's because of its cancellation schematics. 
![alt text](image-62.png)

###  Are there other types of resources?
-  Yep, resource is a lower‑level resource that works with promises. RxResource works with observables. If your application requires RXJS operators such as merge or forkjoin, use rxResource instead. It still retrieves data into a signal with no manual subscription required.
![alt text](image-63.png) 

### What if we need to pass parameters?
- An HTTP request often includes parameters such as a product ID to get details for one product.

# Retrieving Data Reactively

- We retrive data reactivly using signals + Resource API

## Sharing Data in a Service
- Declare signals in a service to share them.
![alt text](image-64.png)

## Reactively Retrueving Data
![alt text](image-65.png)

## Handling Undefined and Passing Parameters with httpResource
- If we return a string from our arrow function, httpResource uses that string to issue an HTTP request. However, if we return undefined, httpResource won't issue a request.
![alt text](image-66.png)

### Options Object version

![alt text](image-67.png)

## httpResource Features and Signal Suggestions
![alt text](image-68.png)

![alt text](image-70.png)

![alt text](image-71.png)

![alt text](image-72.png)

![alt text](image-69.png)

![alt text](image-73.png)

- If we are using angular 16 or 16+
![alt text](image-74.png)
