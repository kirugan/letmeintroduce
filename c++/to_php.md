## How to write static properties
<table>
  <tr>
    <th>
      php
    </th>
    <th>
      c++
    </th>
  </tr>
  <tr>
    <td>
      <pre lang="php">       
class Test {
   static $prop = 34.4;
}
      </pre>
    </td>
    <td>
      <pre lang="c++">

// in *.h file
class Test {
public:
   static int test;
};
// in *.cpp file
int Test::test = 34.4;
      </pre>
    </td>
  </tr>
</table>

Two things that one should note:
1. Initialization is separated from definition (see exceptions) (if you write it in *.h file then there would be N initialization calls = number of includes for this file)
2. Despite of type information availability, we still have to specify type first. See [why](https://stackoverflow.com/questions/29702712/why-do-you-need-to-specify-type-of-extern-static-variable-at-initialization)

Exceptions for separate initilization:

If a static property specified as const **and** type property is int or numeric enum you can use direct initialization:
```c++
class Test {
public:
  static const int prop = 34;
};
```
