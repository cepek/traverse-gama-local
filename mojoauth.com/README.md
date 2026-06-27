# Parse and Generate YAML with C++ 

https://mojoauth.com/parse-and-generate-formats/parse-and-generate-yaml-with-cpp

## Loading and Parsing YAML Files

For instance, consider a ``config.yaml`` file:

    application:
      name: MyAwesomeApp
      version: 1.2.0
    database:
      host: localhost
      port: 5432
  
You'd load it like this:
  
    #include <yaml-cpp/yaml.h>
    #include <fstream>
    #include <iostream>

    int main() {
        YAML::Node config = YAML::Load(std::ifstream("config.yaml"));
        std::string app_name = config["application"]["name"].as<std::string>();
        std::cout << "Application Name: " << app_name << std::endl;
        return 0;
    }

A common pitfall is attempting to access a key that doesn't
exist. This can cause your program to crash. Always verify a node's
existence using ``config["key"].IsDefined()`` before dereferencing it
with ``.as<T>()`` to prevent runtime errors.
