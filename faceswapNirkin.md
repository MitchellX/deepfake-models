# some installation details
1. update your g++/gcc
2. update your cmake (3.11 or newer)
3. when you install boost(1.65 or newer). uninstall the oder one, and update the path
            
        sudo ./b2 --prefix=/usr/local/boost install
        sudo ./b2 --prefix=/usr/include/boost install
