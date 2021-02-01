# Port INI - An [INI file](https://en.wikipedia.org/wiki/INI_file) parser and serializer for C++

# Features
* Cross-platform: works on Windows, Linux, MacOS, Android, iOS, etc
* Multi-encoding: support char, wchar_t, char8_t, char16_t, char32_t
* Header-only: just include portini.h

# Basic
* Starting
```CPP
#include <portini.h>

using Document = portini::GenericDocument<char, false>;
using Section = portini::GenericSection<char, false>;
using Key = portini::GenericKey<char>;
```

* Document Functions
```CPP
ParseFromFile
ParseFromString
SerializeToFile
SerializeToString
```

* Section Functions
```CPP
CreateSection
DeleteSection
HasSection
GetSection
```

* Key Functions
```CPP
CreateKey
DeleteKey
HasKey
GetKey
```

* Value Functions
```CPP
GetValue
SetValue
```

# Advance
* Wide character
```CPP
using DocumentW = portini::GenericDocument<wchar_t, false>;
using SectionW = portini::GenericSection<wchar_t, false>;
using KeyW = portini::GenericKey<wchar_t>;
```

* Stable order for sections and keys
```CPP
using StableDocument = portini::GenericDocument<char, true>;
using StableSection = portini::GenericSection<char, true>;
```

* Range-based for loop
```CPP
// Loop Document
for (auto& sec : doc) {
    std::cout << sec.first << std::endl;
}

// Loop Section
for (auto& key : sec.second) {
    std::cout << key.first << std::endl;
    std::cout << key.second.GetValue() << std::endl;
}
```

* Operator overloading
```CPP
// Get Section
auto& sec = doc["name"];

// Get Key
auto& key = sec["name"];
```

* User-defined conversion function
```CPP
// Get Value
short s = key;
unsigned short us = key;
int i = key;
unsigned int ui = key;
long l = key;
unsigned long ul = key;
float f = key;
double d = key;
auto& str = key;

// Set Value
key = short(0);
key = unsigned short(0);
key = 0;
key = 0U;
key = 0L;
key = 0UL;
key = 0.0F;
key = 0.0;
key = "str";
```

* Move semantics
```CPP
Section sec;
// Fill Section
doc["name"] = std::move(sec);
```

# Contact
[markliprc@foxmail.com](mailto://markliprc@foxmail.com)
