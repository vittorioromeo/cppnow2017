# cppnow2017
Repository for my C++Now 2017 talks.

## Implementing variant visitation using lambdas

> The addition of `std::variant` to the upcoming C++17 standard will introduce a "type-safe sum type" to the Standard Library.
> Variants model a "choice between types" - they essentially are type-safe "tagged unions".
>
> The interface they expose, however, is often more cumbersome to use than it needs to be: defining exhaustive visitors requires the user to create a class with several `operator()` overloads, or to create a chain of > `if constexpr(...)` calls. Both solutions are not very elegant.
>
> After a brief overview of `std::variant` and its usefulness, this talk will focus on the implementation of a "lambda-based in-place visitation" approach, where the user can visit a variant by simply providing a set > of lambdas on the spot. This will require implementing a way of overloading arbitrary function objects.
>
> Recursive variant types will then be covered and the "lambda-based" visitation techniques will be applied to them. This will require implementing the "Y combinator" higher-order function to achieve > zero-runtime-overhead lambda recursion.
>
> This talk is intended for developers familiar with C++11 and C++14 core language features (lambdas, variadic templates, `auto`, etc...). Prior knowledge of `std::variant` or sum types is not required.

* ~YouTube Video~ *(not yet available)*

* [`sched.org` link](https://cppnow2017.sched.com/event/f513597672d99e15edc1cd89f7b7b761)

## You must type it three times

Lightning talk about the fact that code has to be manually copy-pasted three times to achieve `noexcept`-friendliness and SFINAE-friendliness. E.g.

```cpp
template <typename F, typename... Ts>
auto log_and_call(F&& f, Ts&&... xs)
    noexcept(noexcept(
        std::forward<F>(f)(std::forward<Ts>(xs)...)
    ))
-> decltype(
    std::forward<F>(f)(std::forward<Ts>(xs)...)
)
{
    log << "calling `f`\n";
    return std::forward<F>(f)(std::forward<Ts>(xs)...);
}
```

* ~YouTube Video~ *(not yet available)*
