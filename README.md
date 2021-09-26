# STDEASY

Library that simplify to find header for class from STL library.
Instead of searching header for some class you can just include header
with the class name. 

## Table of Contents

* [Example](#example)
* [Inspirations](#inspirations)
* [Presentations](#presentations)

## Example

* Before:

```cpp
#include <utility>

int main()
{
	std::pair<int, int> pair;
	return 0;
}
```

* After:

```cpp
#include <stdeasy/pair>

int main()
{
	std::pair<int, int> pair;
	return 0;
}
```

In this example we just include *pair* header for *std::pair* instaed open
google or cppreference 

[Back to top](#stdeasy)

## Inspirations

* [stdfwd](https://github.com/olegpublicprofile/stdfwd)
* [Qt](https://code.qt.io/cgit/qt/qtbase.git/)

[Back to top](#stdeasy)

## Presentations

* [stdeasy.pdf](docs/slides/stdeasy.pdf)

[Back to top](#stdeasy)


