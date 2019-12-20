cmake_minimum_required(VERSION 3.12 FATAL_ERROR)
project(pytorch_playground)

list(APPEND CMAKE_PREFIX_PATH "C:/Users/Weibel Lab/AppData/Local/conda/conda/envs/Py3/Lib/site-packages/torch")

find_package(Torch REQUIRED)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${TORCH_CXX_FLAGS}")

add_executable(pytorch_playground example-app.cpp)
target_link_libraries(pytorch_playground "${TORCH_LIBRARIES}")
set_property(TARGET pytorch_playground PROPERTY CXX_STANDARD 14)

if (MSVC)
  file(GLOB TORCH_DLLS "${TORCH_INSTALL_PREFIX}/lib/*.dll")
  add_custom_command(TARGET pytorch_playground
					 POST_BUILD
					 COMMAND ${CMAKE_COMMAND} -E copy_if_different
					 ${TORCH_DLLS}
					 $<TARGET_FILE_DIR:pytorch_playground>)
endif (MSVC)