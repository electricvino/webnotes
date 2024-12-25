---
lang: c-sharp
tags:
  - c-sharp
---
https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/async-return-types

Async methods can have the following return types:

- [Task](https://learn.microsoft.com/en-us/dotnet/api/system.threading.tasks.task), for an async method that performs an operation but returns no value.
- [Task<TResult>](https://learn.microsoft.com/en-us/dotnet/api/system.threading.tasks.task-1), for an async method that returns a value.
- `void`, for an event handler.
- Any type that has an accessible `GetAwaiter` method. The object returned by the `GetAwaiter` method must implement the [System.Runtime.CompilerServices.ICriticalNotifyCompletion](https://learn.microsoft.com/en-us/dotnet/api/system.runtime.compilerservices.icriticalnotifycompletion) interface.
- [IAsyncEnumerable<T>](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.iasyncenumerable-1), for an async method that returns an _async stream_.

Use Task instead of void because an async method that returns void cannot be awaited.


**ValueTask:**  Benefits over ref inherent in task is performance for a tight loop, etc.

Because [Task](https://learn.microsoft.com/en-us/dotnet/api/system.threading.tasks.task) and [Task<TResult>](https://learn.microsoft.com/en-us/dotnet/api/system.threading.tasks.task-1) are reference types, memory allocation in performance-critical paths, particularly when allocations occur in tight loops, can adversely affect performance. Support for generalized return types means that you can return a lightweight value type instead of a reference type to avoid more memory allocations.

.NET provides the [System.Threading.Tasks.ValueTask<TResult>](https://learn.microsoft.com/en-us/dotnet/api/system.threading.tasks.valuetask-1) structure as a lightweight implementation of a generalized task-returning value. The following example uses the [ValueTask<TResult>](https://learn.microsoft.com/en-us/dotnet/api/system.threading.tasks.valuetask-1) structure to retrieve the value of two dice rolls.

## Async streams with IAsyncEnumerable<T>

An async method might return an _async stream_, represented by [IAsyncEnumerable<T>](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.iasyncenumerable-1). An async stream provides a way to enumerate items read from a stream when elements are generated in chunks with repeated asynchronous calls. The following example shows an async method that generates an async stream:

C#Copy

```
static async IAsyncEnumerable<string> ReadWordsFromStreamAsync()
{
    string data =
        @"This is a line of text.
              Here is the second line of text.
              And there is one more for good measure.
              Wait, that was the penultimate line.";

    using var readStream = new StringReader(data);

    string? line = await readStream.ReadLineAsync();
    while (line != null)
    {
        foreach (string word in line.Split(' ', StringSplitOptions.RemoveEmptyEntries))
        {
            yield return word;
        }

        line = await readStream.ReadLineAsync();
    }
}
```

The preceding example reads lines from a string asynchronously. Once each line is read, the code enumerates each word in the string. Callers would enumerate each word using the `await foreach` statement. The method awaits when it needs to asynchronously read the next line from the source string.