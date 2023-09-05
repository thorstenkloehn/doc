---
title: "Drogon"
draft: false
type: "page"
menu: 
  main:
    name: "Drogon"
    weight: 7
    
---

# Drogon

Drogon ist ein C++ Webframework, das auf der C++20-Standardbibliothek basiert. Es verwendet die asynchrone Programmierung mit Hilfe von C++20 Coroutinen.

## Drogon Projekt erstellen

```bash
drogon_ctl create project ahrensburgWebsite
cd ahrensburgWebsite
mkdir build
cd build
cmake ..
make
```

## Drogon starten

```bash
./ahrensburgWebsite
```
### CMakeLists.txt ändern
```cmake
find_package(PostgreSQL REQUIRED)
target_link_libraries(${PROJECT_NAME} PRIVATE Drogon::Drogon ${PostgreSQL_LIBRARIES} yaml-cpp)
```

## Beispiel code

```c++
#include <drogon/drogon.h>
#include <yaml-cpp/yaml.h>
#include <postgresql/libpq-fe.h>
int main() {

}
