# Resharp - The C# Essentials Refresher

![C#](https://img.shields.io/badge/C%23-12-239120?logo=csharp&logoColor=white) ![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?logo=dotnet&logoColor=white) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE) ![Modules](https://img.shields.io/badge/modules-17-brightgreen) ![Lines](https://img.shields.io/badge/annotated%20lines-8.5k-brightgreen) ![Dependencies](https://img.shields.io/badge/dependencies-none-success) ![Nullable](https://img.shields.io/badge/nullable-enabled-informational) ![Platforms](https://img.shields.io/badge/platforms-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey)

A working reference for **C# language fundamentals and modern idioms** - 17 runnable
modules, heavily annotated, built for revisiting syntax and preparing for technical
interviews.

## 📌 Overview

This is not a tutorial series. Each module is a single self-contained `.cs` file that
opens with a dense reference header - complexity tables, thread-safety matrices, type
size and range charts, gotcha lists - followed by runnable demonstrations of every
point the header makes. Read the header for the summary, run the module to watch the
behaviour.

It's designed for:

* Engineers returning to C# after time in another stack
* Interview preparation, especially the "what actually happens at runtime" questions
* Anyone wanting a fast answer to *how does this behave again?* with code to prove it

## 🧠 Topics Covered

**Language fundamentals**

* `Basics` — syntax, control flow, method structure
* `DataTypes` — value vs. reference semantics, full size/range/default/suffix table, boxing, `nint`/`nuint`
* `StringManipulation` — immutability, interning, and the concatenation performance hierarchy from `Span<char>` down to `+=` in a loop
* `StructuresNRecords` — structs, records, positional syntax
* `StructuresRules` — interface vs. abstract class vs. struct vs. record vs. sealed: what's declarable, instantiable, inheritable, implementable

**Object orientation**

* `AccessPolymorphism` — every access modifier, `virtual` vs. `new` hiding, override resolution
* `ExtensionMethods` — the five rules, compile-time resolution, why instance methods always win

**Modern C#**

* `AdvancedSyntax` — records, operator overloading, primary constructors, init-only properties, target-typed `new()`, deconstruction, local functions, caller-info attributes, covariant returns, default interface methods
* `NullablePatterns` — nullable value types vs. nullable reference types, all five null operators (`?.` `??` `??=` `!` `is null`), and why NRTs are compile-time only

**Functional and event-driven**

* `FuncAction` — `Func<>`, `Action<>`, predicates
* `DelegatesEvents` — custom delegates, `EventArgs`, multicast invocation, an order-processing pipeline built from them

**Concurrency**

* `AsyncAwait` — the async state machine, `ConfigureAwait`, deadlocks, exception propagation
* `TaskrunVariants` — 15+ forms of `Task.Run`: void lambdas, return values, method groups, deferred await
* `ConcurrentCollections` — thread-safety matrix for every BCL collection, why `Dictionary<K,V>` under concurrent write corrupts rather than merely races, why `GetOrAdd`'s factory isn't atomic, `lock(this)` as antipattern

**Data structures and algorithms**

* `DataStructures` — arrays, `List<T>`, `Dictionary`, `Queue`, `Stack`, `HashSet`, with iteration-strategy tradeoffs
* `SortingAlgos` — bubble, selection, insertion, merge, quick, heap, counting; full best/average/worst/space/stability table

**Error handling**

* `ExceptionsBrush` — custom exception types across a layered repository/service architecture, nested handling, when to catch and when to let it climb

## 🛠️ Requirements

* .NET SDK **8.0** or later
* Any C# IDE:

  * Visual Studio 2022
  * VS Code + C# Dev Kit
  * Rider

No NuGet packages. The whole thing builds against the BCL.

## 🚀 Getting Started

```bash
# Clone the repo
git clone https://github.com/suntosh/Resharp.git

# Navigate into the project
cd Resharp/Refresher

# Build and run
dotnet run --project Refresher
```

## ✍️ How to Use

`Program.cs` is a switchboard. Every module exposes a static `Exec()`; pick one and
run:

```csharp
public static void Main()
{
    // Basics.Exec();
    // DataTypes.Exec();
    // StructuresRules.Exec();
    SortingAlgorithms.SorterShell.Exec();
}
```

Fully-qualified entry points:

| Module | Entry point |
|---|---|
| Basics | `Refresher.Basics.Exec()` |
| DataTypes | `Refresher.DataTypes.Exec()` |
| StringManipulation | `Refresher.StringOps.Exec()` |
| StructuresNRecords | `Refresher.StructuresNRecords.Exec()` |
| StructuresRules | `Refresher.StructuresRules.Exec()` |
| AccessPolymorphism | `Refresher.AccessAndPolymorphism.Exec()` |
| ExtensionMethods | `Refresher.ExtensionMethods.ExtMethods.Exec()` |
| AdvancedSyntax | `Refresher.AdvancedSyntax.Sugar.Exec()` |
| NullablePatterns | `Refresher.NullablePatterns.Exec()` |
| FuncAction | `Refresher.FuncAction.Exec()` |
| DelegatesEvents | `DelegatePatternDemo.DelegatesEvents.Exec()` |
| AsyncAwait | `await Refresher.AsyncAwait.Exec()` |
| TaskrunVariants | `await Refresher.TaskrunVariants.Exec()` |
| ConcurrentCollections | `ConcurrentCollections.CunCollections.Exec(args)` |
| DataStructures | `Refresher.DataStructures.Exec()` |
| SortingAlgos | `SortingAlgorithms.SorterShell.Exec()` |
| ExceptionsBrush | `ExceptionHandling.ExceptionsBrush.Exec()` |

The two `async` modules need `Main` changed to `static async Task Main()`.

Read the header comment first, then run the module and read the output next to the
source. The headers are the reference; the code is the proof.

## 📂 Project Structure

```
Refresher/
  Refresher.sln
  Refresher/
    Refresher.csproj          # net8.0, nullable enable, implicit usings
    Program.cs                # switchboard — uncomment the module you want

    Basics.cs                 # syntax, control flow
    DataTypes.cs              # value/reference semantics, size & range tables
    StringManipulation.cs     # immutability, interning, concat performance
    StructuresNRecords.cs     # structs and records
    StructuresRules.cs        # interface / abstract / struct / record rules

    AccessPolymorphism.cs     # access modifiers, virtual vs new
    ExtensionMethods.cs       # the five rules, resolution order

    AdvancedSyntax.cs         # modern C# idioms
    NullablePatterns.cs       # nullable value types vs NRTs

    FuncAction.cs             # Func, Action, predicates
    DelegatesEvents.cs        # custom delegates, events, multicast

    AsyncAwait.cs             # state machine, ConfigureAwait, deadlocks
    TaskrunVariants.cs        # 15+ forms of Task.Run
    ConcurrentCollections.cs  # thread-safety matrix, Interlocked, striped locks

    DataStructures.cs         # collections and iteration strategies
    SortingAlgos.cs           # 7 sorts with complexity table

    ExceptionsBrush.cs        # layered architecture, custom exception types

    Assets/                   # supporting notes (indexing, architecture)
```
## 🚧 Roadmap

Modules in progress:

* `LinqEssentials` — deferred vs. immediate execution, query vs. method syntax,
  `IEnumerable` vs. `IQueryable` and the provider boundary, multiple-enumeration
  traps, custom operators
* `Generics` — type parameters and inference, all constraint kinds, covariance
  and contravariance, open vs. closed types, static members per closed type

LINQ and generics currently appear incidentally across `DataStructures`,
`ExtensionMethods` and `AsyncAwait` as tools rather than as subjects. These two
modules will cover them directly.

## 🎯 Goals

* Reinforce core C# semantics — not just syntax, but what the runtime does
* Cover the modern surface area: records, NRTs, primary constructors, pattern matching
* Make concurrency behaviour observable rather than theoretical
* Keep every claim in a comment backed by code that demonstrates it

## 📚 Resources

* Microsoft Docs: [https://learn.microsoft.com/en-us/dotnet/csharp/](https://learn.microsoft.com/en-us/dotnet/csharp/)
* C# Language Reference
* .NET API Browser

## 🤝 Contributing

Pull requests are welcome — additional modules, corrections, or clearer examples.

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
