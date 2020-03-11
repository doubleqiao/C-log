# C++-log
Knowledge learned during learning C++

- 1.The comment about /* and */ actually find the nearest */ to end the comment. Not matter the */ is in a double quatation or not.
For example: 
/ *  " * / " /
will actually be
"/

- 2.The "i" in the “for” loop is only valid inside the for loop.

- 3.Sometimes the compilation failed and there is no error in the source file, maybe it is because some symbols are under the Chinese input state. -_-||

- 4.Small mistakes matter! Pay attention to the sequence of the input arguments of the function.

- 5.Using catkin to compile, if there is an error like 
"CMake Error at /opt/ros/kinetic/share/catkin/cmake/catkinConfig.cmake:83 (find_package):
  Could not find a package configuration file provided by "alglib" with any
  of the followings:

    alglibConfig.cmake
    alglib-config.cmake

  Add the installation prefix of "alglib" to CMAKE_PREFIX_PATH or set
  "alglib_DIR" to a directory containing one of the above files.  If "alglib"
  provides a separate development package or SDK, be sure it has been
  installed."
  
  or something like that, probably because the dependency of package "alglib" is not included in the package.xml. Or the package/library alglib is not installed so it can not be found.
  
- 6.When using gtest to test the results, catkin_make only generates the excutable and library targets, while catkin_make run_tests will generate the gtest target. Then the gtest target can be implemented similar as the "node" using rosrun.

- 7.When using multiple workspace, overlay could solve the problem of the connection between different workspaces. However, it is recommended to use only one workspace. (Still there is one problem)

- 8.needs some initial values before assignment? use the member function setcontent to initialize the content.

- 9.Error about Eigen:

/usr/include/eigen3/Eigen/src/Core/DenseCoeffsBase.h: In instantiation of ‘Eigen::DenseCoeffsBase<Derived, 1>::Scalar& Eigen::DenseCoeffsBase<Derived, 1>::operator[](Eigen::Index) [with Derived = Eigen::Matrix<double, -1, -1>; Eigen::DenseCoeffsBase<Derived, 1>::Scalar = double; Eigen::Index = long int]’:
main.cpp:37:21:   required from here
/usr/include/eigen3/Eigen/src/Core/util/StaticAssert.h:119:9: error: ‘THE_BRACKET_OPERATOR_IS_ONLY_FOR_VECTORS__USE_THE_PARENTHESIS_OPERATOR_INSTEAD’ is not a member of ‘Eigen::internal::static_assertion<false>’
         if (Eigen::internal::static_assertion<static_cast<bool>(CONDITION)>::MS
         ^
/usr/include/eigen3/Eigen/src/Core/DenseCoeffsBase.h:394:7: note: in expansion of macro ‘EIGEN_STATIC_ASSERT’
       EIGEN_STATIC_ASSERT(Derived::IsVectorAtCompileTime.
  
  Such error is because using the BRACKET for the Eigen matrix. So using parenthesis instead.
- 10.When using std::vector<> and its corresponding function "push_back", do not forget to "clear" the vector when it is necessary.
- 11.Dependency: crobot_element -> crobot -> EKF  
  Wrong practice "crobot_element, crobot -> EKF"  
  Right practice "crobot_element -> crobot", "crobot -> EKF"  
  Check the dependency tree.
  
- 12.sensor_msgs::PointCloud needs to be resized before you could properly use them. I guess.

- 13.The name of package or the workspace should avoid space, otherwise it may cause error while compiling.
