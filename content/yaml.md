---
title: "Yaml"
draft: false
type: "page"
menu: 
  main:
    name: "Yaml"
    weight: 5
    
---
# Yaml
Yaml ist eine einfache Auszeichnungssprache, die für die Konfiguration von Programmen verwendet wird. 
Sie ist eine Alternative zu XML und JSON.

## Syntax
Yaml verwendet Einrückungen, um die Struktur des Dokuments zu definieren.
```yaml
# Beispiel
name: "Max Mustermann"
age: 42
```
## Installation auf Ubuntu c++
```bash
sudo apt-get install libyaml-cpp-dev
```

### Beispiel code
```c++
#include <iostream>
#include <yaml-cpp/yaml.h>

int main() {
 // Load the YAML document from a file
  YAML::Node config = YAML::LoadFile("../config.yaml");

  // Access the name field
  std::string name = config["name"].as<std::string>();

  // Print the name
  std::cout << "Name: " << name << std::endl;

  return 0;

}
```

### cmake
```cmake
cmake_minimum_required(VERSION 3.15)
project(start)

set(CMAKE_CXX_STANDARD 14)
find_package(yaml-cpp REQUIRED)
add_executable(start main.cpp)
target_link_libraries(start yaml-cpp)
```

### Beispiel yaml Datei
```yaml
# Beispiel
name : "Thorsten"

