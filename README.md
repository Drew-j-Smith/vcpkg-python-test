# vcpkg-python-test

This (tries) to run python in c++ using vcpkg to install python.

To replicate run:

    git clone --recurse-submodules https://github.com/Drew-j-Smith/vcpkg-python-test
    cd vcpkg-python-test
    mkdir build
    cd build
    cmake ..
    cmake --build .
    {platform-dependent-executable}

Everything compiles and links, but when the executable is run it produces this error:

    Python path configuration:
      PYTHONHOME = (not set)
      PYTHONPATH = (not set)
      program name = 'C:\Users\smith\OneDrive\Desktop\OSU\vcpkg-python-test\build\Debug\test.exe'
      isolated = 0
      environment = 1
      user site = 1
      import site = 1
      sys._base_executable = 'C:\\Users\\smith\\OneDrive\\Desktop\\OSU\\vcpkg-python-test\\build\\Debug\\test.exe'
      sys.base_prefix = ''
      sys.base_exec_prefix = ''
      sys.platlibdir = 'lib'
      sys.executable = 'C:\\Users\\smith\\OneDrive\\Desktop\\OSU\\vcpkg-python-test\\build\\Debug\\test.exe'      
      sys.prefix = ''
      sys.exec_prefix = ''
      sys.path = [
        'C:\\Users\\smith\\OneDrive\\Desktop\\OSU\\vcpkg-python-test\\build\\Debug\\python310_d.zip',
        '.\\DLLs',
        '.\\lib',
        'C:\\Users\\smith\\OneDrive\\Desktop\\OSU\\vcpkg-python-test\\build\\Debug',
      ]
    Fatal Python error: init_fs_encoding: failed to get the Python codec of the filesystem encoding
    Python runtime state: core initialized
    ModuleNotFoundError: No module named 'encodings'
    
    Current thread 0x000062bc (most recent call first):
      <no Python frame>