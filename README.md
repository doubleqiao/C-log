# C++-log
Knowledge learned during learning C++

- 1.The comment about /* and */ actually find the nearest */ to end the comment. Not matter the */ is in a double quatation or not.
For example: 
/ *  " * / " /
will actually be
"/

- 2.The "i" in the “for” loop is only valid inside the for loop.

- 3.Sometimes the compilation failed and there is no errors in the source file, maybe it is because some symbols are under the Chinese input state. -_-||

- 4.Small mistakes matter! Pay attention to the sequence of the input arguments of the function.

- 5.Using catkin to compile, if there is an error like 
"CMake Error at /opt/ros/kinetic/share/catkin/cmake/catkinConfig.cmake:83 (find_package):
  Could not find a package configuration file provided by "alglib" with any
  of the following names:

    alglibConfig.cmake
    alglib-config.cmake

  Add the installation prefix of "alglib" to CMAKE_PREFIX_PATH or set
  "alglib_DIR" to a directory containing one of the above files.  If "alglib"
  provides a separate development package or SDK, be sure it has been
  installed."
  
  or something like that, probably because the dependency of package "alglib" is not included in the package.xml. 
  
- 6. When using gtest to test the results, catkin_make only generates the excutable and library targets, while catkin_make run_tests will generate the gtest target. Thne the gtest target can be implemented similar as the "node" using rosrun.
