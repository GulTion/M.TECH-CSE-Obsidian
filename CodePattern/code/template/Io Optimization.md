---
code_type: template
---
```cpp
// The following block might trivially improve the exec time.
static const auto __optimize__ = []() {
    std::ios::sync_with_stdio(false);
    std::cin.tie(NULL);
    return 0;
}();
```