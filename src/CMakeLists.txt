if (WIN32)
  add_executable(${EXECUTABLE_TITLE} "rsgain.c" "scan.cpp" "output.c" "tag.cpp" "easymode.cpp" "${PROJECT_BINARY_DIR}/rsgain.manifest")
else()
  add_executable(${EXECUTABLE_TITLE} "rsgain.c" "scan.cpp" "output.c" "tag.cpp" "easymode.cpp")

  # GCC 10 requires linking with pthread for some reason
  if (CMAKE_COMPILER_IS_GNUCC AND CMAKE_CXX_COMPILER_VERSION VERSION_LESS 11)
    target_link_libraries(${EXECUTABLE_TITLE} pthread)
  endif ()
endif()
set (EXECUTABLE_OUTPUT_PATH "${PROJECT_BINARY_DIR}")



  
