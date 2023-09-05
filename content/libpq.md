---
title: "Libpq"
draft: false
type: "page"
menu: 
  main:
    name: "Libpq"
    weight: 6
    
---
# Libpq
Libpq ist eine Bibliothek, die es ermöglicht, mit PostgreSQL-Datenbanken zu kommunizieren.
## Installation auf Ubuntu c++
```bash
sudo apt-get install libpq-dev
```
## CMakelists.txt
```cmake
cmake_minimum_required(VERSION 3.15)
project(start)

set(CMAKE_CXX_STANDARD 14)

find_package(PostgreSQL REQUIRED)

add_executable(start main.cpp)

target_link_libraries(start ${PostgreSQL_LIBRARIES} yaml-cpp)
```
## Beispiel code
```c++
#include <iostream>
#include <yaml-cpp/yaml.h>
#include <postgresql/libpq-fe.h>

int main() {
 // Load the YAML document from a file
  YAML::Node config = YAML::LoadFile("../config.yaml");

  // Extract the configuration values
  std::string host = config["host"].as<std::string>();
  int port = config["port"].as<int>();
  std::string database = config["database"].as<std::string>();
  std::string user = config["user"].as<std::string>();
  std::string password = config["password"].as<std::string>();

  // Connect to the database
  PGconn* conn = PQsetdbLogin(host.c_str(), std::to_string(port).c_str(), nullptr, nullptr, database.c_str(), user.c_str(), password.c_str());
  if (PQstatus(conn) != CONNECTION_OK) {
    std::cerr << "Connection to database failed: " << PQerrorMessage(conn) << std::endl;
    PQfinish(conn);
    return 1;
  }
  return 0;
}
```
## Beispiel yaml Datei
```yaml
host: localhost
port: 5432
database: thorsten
user: thorsten
password: Test
```



