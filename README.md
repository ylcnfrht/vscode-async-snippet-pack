## Async Snippet Pack for Visual Studio Code

#### A snippet pack to make you more productive working with Async library.


![](async.gif)


#### Here's the full list of all the snippets:

### Shortcuts / Commands

| Command | Description |
| --- | --- |
| .concat | Applies iteratee to each item in coll, concatenating the results. Returns the concatenated list. The iteratees are called in parallel, and the results are concatenated as they return. There is no guarantee that the results array will be returned in the original order of coll passed to the iteratee function |
| .detect | Returns the first value in coll that passes an async truth test. The iteratee is applied in parallel, meaning the first iteratee to return true will fire the detect callback with that result. That means the result might not be the first item in the original coll (in terms of order) that passes the test. If order within the original coll is important |
| .each | Applies the function iteratee to each item in coll, in parallel. The iteratee is called with an item from the list, and a callback for when it has finished. If the iteratee passes an error to its callback, the main callback (for the each function) is immediately called with the error. Note, that since this function applies iteratee to each item in parallel, there is no guarantee that the iteratee functions will complete in order |
| .forEachOf | Like each, except that it passes the key (or index) as the second argument to the iteratee. |
| .every | Returns true if every element in coll satisfies an async test. If any iteratee call returns false, the main callback is immediately called. |
| .groupBy | Returns a new object, where each value corresponds to an array of items, from coll, that returned the corresponding key. That is, the keys of the object correspond to the values passed to the iteratee callback. Note: Since this function applies the iteratee to each item in parallel, there is no guarantee that the iteratee functions will complete in order. However, the values for each key in the result will be in the same order as the original coll. For Objects, the values will roughly be in the order of the original Objects' keys (but this can vary across JavaScript engines). |
| .map | Produces a new collection of values by mapping each value in coll through the iteratee function. The iteratee is called with an item from coll and a callback for when it has finished processing. Each of these callback takes 2 arguments: an error, and the transformed item from coll. If iteratee passes an error to its callback, the main callback (for the map function) is immediately called with the error. Note, that since this function applies the iteratee to each item in parallel, there is no guarantee that the iteratee functions will complete in order. However, the results array will be in the same order as the original coll. If map is passed an Object, the results will be an Array. The results will roughly be in the order of the original Objects' keys (but this can vary across JavaScript engines). |
| .mapValues | A relative of map, designed for use with objects. Produces a new Object by mapping each value of obj through the iteratee function. The iteratee is called each value and key from obj and a callback for when it has finished processing. Each of these callbacks takes two arguments: an error, and the transformed item from obj. If iteratee passes an error to its callback, the main callback (for the mapValues function) is immediately called with the error. Note, the order of the keys in the result is not guaranteed. The keys will be roughly in the order they complete, (but this is very engine-specific)|
| .some | Returns true if at least one element in the coll satisfies an async test. If any iteratee call returns true, the main callback is immediately called. |
| .sortBy | Sorts a list by the results of running each coll value through an async iteratee. |
| .transform | A relative of reduce. Takes an Object or Array, and iterates over each element in series, each step potentially mutating an accumulator value. The type of the accumulator defaults to the type of collection passed in. |
| .applyEach | Applies the provided arguments to each function in the array, calling callback after all functions have completed. If you only provide the first argument, fns, then it will return a function which lets you pass in the arguments as if it were a single function call. If more arguments are provided, callback is required while args is still optional. |
| .auto | Determines the best order for running the AsyncFunctions in tasks, based on their requirements. Each function can optionally depend on other functions being completed first, and each function is run as soon as its requirements are satisfied. If any of the AsyncFunctions pass an error to their callback, the auto sequence will stop. Further tasks will not execute (so any other functions depending on it will not run), and the main callback is immediately called with the error. AsyncFunctions also receive an object containing the results of functions which have completed so far as the first argument, if they have dependencies. If a task function has no dependencies, it will only be passed a callback. |
| .autoInject | A dependency-injected version of the async.auto function. Dependent tasks are specified as parameters to the function, after the usual callback parameter, with the parameter names matching the names of the tasks it depends on. This can provide even more readable task graphs which can be easier to maintain. If a final callback is specified, the task results are similarly injected, specified as named parameters after the initial error parameter. The autoInject function is purely syntactic sugar and its semantics are otherwise equivalent to async.auto. |
| .cargo | Creates a cargo object with the specified payload. Tasks added to the cargo will be processed altogether (up to the payload limit). If the worker is in progress, the task is queued until it becomes available. Once the worker has completed some tasks, each callback of those tasks is called. Check out these animations for how cargo and queue work. While queue passes only one task to one of a group of workers at a time, cargo passes an array of tasks to a single worker, repeating when the worker is finished. |
| .during | Like whilst, except the test is an asynchronous function that is passed a callback in the form of function (err, truth). If error is passed to test or fn, the main callback is immediately called with the value of the error. |
| .forever | Calls the asynchronous function fn with a callback parameter that allows it to call itself again, in series, indefinitely. If an error is passed to the callback then errback is called with the error, and execution stops, otherwise it will never be called. |
| .parallel | Run the tasks collection of functions in parallel, without waiting until the previous function has completed. If any of the functions pass an error to its callback, the main callback is immediately called with the value of the error. Once the tasks have completed, the results are passed to the final callback as an array. Note: parallel is about kicking-off I/O tasks in parallel, not about parallel execution of code. If your tasks do not use any timers or perform any I/O, they will actually be executed in series. Any synchronous setup sections for each task will happen one after the other. JavaScript remains single-threaded. Hint: Use reflect to continue the execution of other tasks when a task fails. It is also possible to use an object instead of an array. Each property will be run as a function and the results will be passed to the final callback as an object instead of an array. This can be a more readable way of handling results from async.parallel. |
| .queue | Creates a queue object with the specified concurrency. Tasks added to the queue are processed in parallel (up to the concurrency limit). If all workers are in progress, the task is queued until one becomes available. Once a worker completes a task, that task's callback is called. |
| .race | Runs the tasks array of functions in parallel, without waiting until the previous function has completed. Once any of the tasks complete or pass an error to its callback, the main callback is immediately called. It's equivalent to Promise.race(). |
| .retry | Attempts to get a successful response from task no more than times times before returning an error. If the task is successful, the callback will be passed the result of the successful task. If all attempts fail, the callback will be passed the error and result (if any) of the final attempt. |
| .retryable | A close relative of retry. This method wraps a task and makes it retryable, rather than immediately calling it with retries. |
| .seq | Version of the compose function that is more natural to read. Each function consumes the return value of the previous function. It is the equivalent of compose with the arguments reversed. Each function is executed with the this binding of the composed function. |
| .series | Run the functions in the tasks collection in series, each one running once the previous function has completed. If any functions in the series pass an error to its callback, no more functions are run, and callback is immediately called with the value of the error. Otherwise, callback receives an array of results when tasks have completed. It is also possible to use an object instead of an array. Each property will be run as a function, and the results will be passed to the final callback as an object instead of an array. This can be a more readable way of handling results from async.series. Note that while many implementations preserve the order of object properties, the ECMAScript Language Specification explicitly states that  'The mechanics and order of enumerating the properties is not specified.'  So if you rely on the order in which your series of functions are executed, and want this to work on all platforms, consider using an array. |
| .tryEach | It runs each task in series but stops whenever any of the functions were successful. If one of the tasks were successful, the callback will be passed the result of the successful task. If all tasks fail, the callback will be passed the error and result (if any) of the final attempt. |
| .waterfall | Runs the tasks array of functions in series, each passing their results to the next in the array. However, if any of the tasks pass an error to their own callback, the next function is not executed, and the main callback is immediately called with the error. |
| .whilst | Repeatedly call iteratee, while test returns true. Calls callback when stopped, or an error occurs. |
| .apply | Creates a continuation function with some arguments already applied. Useful as a shorthand when combined with other control flow functions. Any arguments passed to the returned function are added to the arguments originally passed to apply. |
| .asyncify | Take a sync function and make it async, passing its return value to a callback. This is useful for plugging sync functions into a waterfall, series, or other async functions. Any arguments passed to the generated function will be passed to the wrapped function (except for the final callback argument). Errors thrown will be passed to the callback. If the function passed to asyncify returns a Promise, that promises's resolved/rejected state will be used to call the callback, rather than simply the synchronous return value. This also means you can asyncify ES2017 async functions.|
| .constant | Returns a function that when called, calls-back with the values provided. Useful as the first function in a waterfall, or for plugging values in to auto. |
| .dir | Logs the result of an async function to the console using console.dir to display the properties of the resulting object. Only works in Node.js or in browsers that support console.dir and console.error (such as FF and Chrome). If multiple arguments are returned from the async function, console.dir is called on each argument in order. |
| .ensureAsync | Wrap an async function and ensure it calls its callback on a later tick of the event loop. If the function already calls its callback on a next tick, no extra deferral is added. This is useful for preventing stack overflows (RangeError: Maximum call stack size exceeded) and generally keeping Zalgo contained. ES2017 async functions are returned as-is -- they are immune to Zalgo's corrupting influences, as they always resolve on a later tick. |
| .log | Logs the result of an async function to the console. Only works in Node.js or in browsers that support console.log and console.error (such as FF and Chrome). If multiple arguments are returned from the async function, console.log is called on each argument in order. |
| .memoize | Caches the results of an async function. When creating a hash to store function results against, the callback is omitted from the hash and an optional hash function can be used. If no hash function is specified, the first argument is used as a hash key, which may work reasonably if it is a string or a data type that converts to a distinct string. Note that objects and arrays will not behave reasonably. Neither will cases where the other arguments are significant. In such cases, specify your own hash function. The cache of results is exposed as the memo property of the function returned by memoize.|
| .nextTick | Calls callback on a later loop around the event loop. In Node.js this just calls process.nextTick. In the browser it will use setImmediate if available, otherwise setTimeout(callback, 0), which means other higher priority events may precede the execution of callback. This is used internally for browser-compatibility purposes. |
| .reflect | Wraps the async function in another function that always completes with a result object, even when it errors. The result object has either the property error or value.|
| .reflectAll | A helper function that wraps an array or an object of functions with reflect. |
| .setImmediate | Calls callback on a later loop around the event loop. In Node.js this just calls setImmediate. In the browser it will use setImmediate if available, otherwise setTimeout(callback, 0), which means other higher priority events may precede the execution of callback. |
| .timeout | Sets a time limit on an asynchronous function. If the function does not call its callback within the specified milliseconds, it will be called with a timeout error. The code property for the error object will be 'ETIMEDOUT'. |


### For example 

.waterfall


```
async.waterfall([
  function(callback) {
    callback(null, 'one', 'two');
  },
  function(arg1, arg2, callback) {
    callback(null, 'three');
  },
  function(arg1, callback) {
    callback(null, 'done');
  }
], function (err, result) {
  // result now equals 'done'
});


```


## Release Notes

Users appreciate release notes as you update your extension.


## For more information

https://caolan.github.io/async/



### 1.0.0

Initial release of async snippets

### 1.0.1

Deleted unnecessary comment line and examples


-----------------------------------------------------------------------------------------------------------

