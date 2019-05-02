# PySFML - Python bindings for SFML

This is fork of https://github.com/Sonkun/python-sfml

These bindings officially support Python 2.7 and the latest versions of Python 3.x but we encourage you to use the latter one. Incidentally, the documentation, tutorials and examples are written in the latest version of Python.

Please visit the website (https://www.python-sfml.org/) for any complementary information on this project. Also, feel free to email us with any questions or concerns.

* Jonathan De Wachter <dewachter.jonathan@gmail.com>
* Edwin Marshall      <emarshall85@gmail.com>

You're also encouraged to visit (and contribute) to the wiki which gathers various piece of code, tutorials, tips and tricks.

These bindings were created in large part by **Jonathan De Wachter**, with significant contributions from **Edwin Marshall**. Thanks a lot to **James Cowgill** who occasionally fixes broken builds and maintains Debian packages. Other contributors include **Jorge Araya Navarro** and **Richard Sims**.

# Why fork?

- Fix compilation errors (particulary on windows10/mingw64)
- Fix binding erros (if some)
- Add my own improvements

# How 2 build on Windows10/mingw64

1. download [sfml 2.3.2](https://www.sfml-dev.org/download/sfml/2.3.2/)
2. use suggested mingw compiler [4.9.2](https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Personal%20Builds/mingw-builds/4.9.2/threads-posix/seh/x86_64-4.9.2-release-posix-seh-rt_v4-rev2.7z/download)

3. fix python sources to be able to use new `vcruntime140` instead of `msvcrXXX`
    * goto python installation folder
    * goto `cygwincompiler.py` `get_msvcr` function
    * add yet one `elif` or `else` statement and make `return ['vcruntime140']`
    * add `vcruntime140.dll` to `libs` forlder in python installation fodler 
        * you can find `vcruntime140.dll` at `windows/system32`
4. build with following command

```
py setup.py build_ext -DMS_WIN64 --compiler=mingw32 --include-dirs path\to\sfml\include --library-dirs path\to\sfml\lib
``` 

5. install

```
py setup.py install
```

## Known Issues

* `audio` module throws errors on import.