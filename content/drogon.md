---
title: "Drogon"
draft: false
type: "page"
menu: 
  main:
    name: "Drogon"
    weight: 7
    
---

# Drogon Core C++
Drogon Core ist ein C++-Framework für die Entwicklung von Webanwendungen. Es ist eine Alternative zu Node.js und Spring Boot.


## cmake
  
  ```cmake
  cmake_minimum_required(VERSION 3.15)
project(start)

set(CMAKE_CXX_STANDARD 14)

# Find the required libraries
find_package(libpq REQUIRED)
find_package(PostgreSQL REQUIRED)
find_package(yaml-cpp REQUIRED)
find_package(drogon REQUIRED)

# Add the executable
add_executable(drogon_example main.cpp)

# Link against the required libraries
target_link_libraries(start ${PostgreSQL_LIBRARIES} yaml-cpp drogon)
```

## Beispiel code

```c++
#include <iostream>
#include <yaml-cpp/yaml.h>
#include <drogon/drogon.h>
#include <libpq-fe.h>

int main() {
  // Load the YAML document from a file
  YAML::Node config = YAML::LoadFile("config.yaml");

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

  // Create a Drogon app
  auto app = drogon::createApp();

  // Add a route to handle HTTP requests
  app->registerHandler("/hello", [](const drogon::HttpRequestPtr& req, std::function<void(const drogon::HttpResponsePtr&)>&& callback) {
    auto res = drogon::HttpResponse::newHttpResponse();
    res->setBody("Hello, world!");
    callback(res);
  });

  // Start the app
  app->run();

  // Clean up
  PQfinish(conn);

  return 0;
}
```
### Beispiel yaml Datei
```yaml
host: localhost
port: 5432
database: mydb
user: myuser
password: mypassword
```



