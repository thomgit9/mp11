[![Documented with Setinstone.io](https://img.shields.io/badge/⛰️Documented%20with-Setinstone.io-success?logo=book&logoColor=white)](https://calendly.com/set-in-stone-thomas-benoit/setinstone-demo)

# Mp11, a C++11 metaprogramming library

## Presentation

**Mp11** is a modern **C++11 metaprogramming library** based on template aliases and variadic templates.  
It provides high‑performance, type‑safe compile‑time computation tools using the concepts presented in:

- [“Simple C++11 metaprogramming”](https://www.boost.org/libs/mp11/doc/html/simple_cxx11_metaprogramming.html)
- [“Simple C++11 metaprogramming (Part 2)”](https://www.boost.org/libs/mp11/doc/html/simple_cxx11_metaprogramming_2.html)

Starting from **Boost 1.66.0**, Mp11 is an official part of the Boost C++ Libraries.  
However, it has **no Boost dependencies** and can be used **standalone** or as a **Git submodule** in your own projects.

Supported integration modes:

- Direct include of headers in `include/boost/mp11`
- Installation through **CMake** (`add_subdirectory`, `find_package(boost_mp11)`)
- Integration within the Boost build system (B2 / Jam)

Repository: [https://github.com/thomgit9/mp11](https://github.com/thomgit9/mp11)

Maintained primarily by [Peter Dimov](https://github.com/pdimov) and the Boost community.

---

## Installation

### Option 1 — Standalone (Header‑only)
```bash
git clone https://github.com/thomgit9/mp11.git
cd mp11
```
Simply add the `include` directory to your project’s header search path:
```cmake
include_directories(${CMAKE_SOURCE_DIR}/mp11/include)
```

### Option 2 — CMake Integration

Add Mp11 as a **subdirectory**:
```cmake
add_subdirectory(mp11)
target_link_libraries(your_target PRIVATE boost_mp11)
```

or install and use **find_package**:
```bash
cmake -DCMAKE_INSTALL_PREFIX=/usr/local .
make install
```
```cmake
find_package(boost_mp11 REQUIRED)
target_link_libraries(your_target PRIVATE boost_mp11)
```

### Option 3 — Within Boost
If you are using Boost as a project dependency:
```bash
b2 headers
b2 libs/mp11/test
```

---

## Usage

Mp11 provides ready‑to‑use compile‑time metafunctions and algorithms that operate on **type lists**, **integral constants**, and **tuples**.  
Core capabilities include:

- Type transformation (`mp_transform`)
- Compile‑time algorithms (`mp_sort`, `mp_append`, `mp_unique`)
- Functional composition and higher‑order metafunctions (`mp_bind`, `mp_quote`)
- Integral and sequence manipulation (`mp_iota`, `mp_plus`, `mp_fold`)

Example use:

```cpp
#include <boost/mp11.hpp>
#include <type_traits>

using namespace boost::mp11;

using L1 = mp_list<int, float>;
using L2 = mp_push_back<L1, double>;  // Result: mp_list<int, float, double>

static_assert(mp_size<L2>::value == 3, "Metaprogramming works!");
```

---

## Main Functions and Classes

| name | file | description | inputs | outputs |
|---|---|---|---|---|
| `mp_list` | `include/boost/mp11/list.hpp` | Defines a compile-time type list | Type pack | Compile-time list type |
| `mp_append` | `include/boost/mp11/algorithm.hpp` | Concatenates multiple type lists | `mp_list...` | Combined `mp_list` |
| `mp_transform` | `include/boost/mp11/algorithm.hpp` | Applies a metafunction to each element of a type list | `Fn`, `mp_list<Ts...>` | `mp_list<Fn<Ts>...>` |
| `mp_map_find` | `include/boost/mp11/map.hpp` | Finds a value by key in a type map | `mp_list<pair<key,value>>`, `key` | `pair` |
| `mp_fold` | `include/boost/mp11/algorithm.hpp` | Left fold (reduce) operation on a type list | List, initial state, operation | Result type |
| `mp_set_union` | `include/boost/mp11/set.hpp` | Combine multiple sets of types into one without duplicates | Set lists | Union set |
| `mp_iota` | `include/boost/mp11/integer_sequence.hpp` | Generates a sequence of integral constants | Integer `N` | `integer_sequence` |
| `mp_integral` | `include/boost/mp11/integral.hpp` | Defines integral constant metafunctions | Value | Type-based constant |
| `mp_lambda` | `include/boost/mp11/lambda.hpp` | Creates composable metafunctions from arbitrary expressions | Expression template | Callable metafunction |
| `mp_with_index` | `include/boost/mp11/detail/mp_with_index.hpp` | Invokes a callable indexed over compile-time range | `N`, callable | Invocation result |

---

## Supported Compilers

- g++ 4.8 or later  
- clang++ 3.9 or later  
- Visual Studio 2013 or later  

Automatically tested via:
- [GitHub Actions](https://github.com/boostorg/mp11/actions)
- [Appveyor (Windows CI)](https://ci.appveyor.com/project/pdimov/mp11)

---

## License

Distributed under the [Boost Software License, Version 1.0](http://boost.org/LICENSE_1_0.txt).  
© 2016‑2025 Peter Dimov and contributors.

---

## Contributors

- [pdimov](https://github.com/pdimov) — 814 commits  
- [grafikrobot](https://github.com/grafikrobot) — 10 commits  
- [joaquintides](https://github.com/joaquintides) — 7 commits  
- [k3DW](https://github.com/k3DW) — 6 commits  
- [glenfe](https://github.com/glenfe) — 6 commits  
- [grisumbras](https://github.com/grisumbras) — 4 commits  
- [theZiz](https://github.com/theZiz) — 3 commits  
- [zerotypos-found](https://github.com/zerotypos-found) — 2 commits  
- [slymz](https://github.com/slymz) — 2 commits  
- [breese](https://github.com/breese) — 2 commits  
- [bernhardmgruber](https://github.com/bernhardmgruber) — 2 commits  
- plus 8 more occasional contributors  

Last commit: [`fe74474`](https://github.com/thomgit9/mp11/commit/fe7447470d96b80eefed91b6206a4a240b664b73) — *Update cuda-windows job in ci.yml* (Nov 03, 2025)  
Author: [Peter Dimov](https://github.com/pdimov)

---

## ⛰️ Documented With SetinStone.io
Focus on the only task that matters: building your codebase!  
With every developer push, Set In Stone’s Mirror Documentation Agent updates your README.md via a pull request — ready for you to review, edit, and approve.

[Book a demo](https://calendly.com/set-in-stone-thomas-benoit/setinstone-demo)