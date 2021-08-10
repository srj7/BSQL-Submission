# [BINARY SQUIRREL](https://binarysquirrel.cf)


![Product image](https://github.com/srj7/Binary-Squirrel-Website-PWA/blob/main/images/BSQL.png?raw=true)

**Binary Squirrel** lets you run snippets of code on devices with slow internet connection. It's also a PWA and can be installed in various devies to improve efficiency. Take a look at the files to see how easily it can be done. It uses template from Creative Tim and modified the values to work based on the needs.

- C
- C++
- Java
- JavaScript (Node.js)
- Python 2
- Python 3
- Ruby
- PHP 7
- Lua 5.1
- Lua 5.2
- Lua 5.3
- Go

# The Sandbox

Whenever code is sent to the bot for execution, an ephemeral Docker container is spawned. This container is running the image found in the docker-image folder. It runs Alpine 3.9 with all the necessary compilers and interpreters to run the code sent to the bot. In addition, the container has extra restrictions:

Limited amount of RAM (64MB)
Limited amount of PIDs (100)
No virtual network card attached
20 second execution time limit
This allows arbitrary code to be safely run within the container without having access to host resources.

![Screenshot](https://github.com/srj7/Binary-Squirrel-Website-PWA/blob/main/images/mainpage.png?raw=true)
