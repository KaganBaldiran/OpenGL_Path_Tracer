cmake_minimum_required(VERSION 3.10)

set(PROJECT_NAME PathTracer)

project(${PROJECT_NAME} VERSION 1.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set_property(GLOBAL PROPERTY USE_FOLDERS ON)

file(GLOB_RECURSE SRC src/*.h src/*.hpp src/*.cpp src/Shaders/* include/Imgui/* include/ImGuizmo-1.83/*)
add_executable(${PROJECT_NAME} src/Main.cpp ${SRC})
include_directories(include/glm include/nlohmann src include/Imgui include/ImGuizmo-1.83) 

add_compile_definitions(IMGUI_DEFINE_MATH_OPERATORS)

if(WIN32)
    foreach(FILE ${SRC}) 
        get_filename_component(PARENT_DIR "${FILE}" DIRECTORY)

        string(REPLACE "${CMAKE_CURRENT_SOURCE_DIR}" "" GROUP "${PARENT_DIR}")

        string(REPLACE "/" "\\" GROUP "${GROUP}")

        if ("${FILE}" MATCHES ".*\\.cpp")
        set(GROUP "Source Files${GROUP}")
        elseif("${FILE}" MATCHES ".*\\.h" OR "${FILE}" MATCHES ".*\\.hpp")
        set(GROUP "Header Files${GROUP}")
        endif()

        source_group("${GROUP}" FILES "${FILE}")
    endforeach()

    set_target_properties(
        ${PROJECT_NAME} PROPERTIES
        VS_DEBUGGER_WORKING_DIRECTORY "$(SolutionDir)..\\src")

    set_target_properties(${PROJECT_NAME} PROPERTIES
        VS_DEBUGGER_ENVIRONMENT "PATH=$(SolutionDir)..\\dlls;%PATH%"
    )    

    include_directories(external/FusionFrameEngine/Include external/oidn-2.3.0.x64.windows/include external/freeimage/include/Source external/glfw-3.3.7.bin.WIN64/glfw-3.3.7.bin.WIN64/include/GLFW external/glew-2.1.0-win32/glew-2.1.0/include/GL external/assimp/include)
    target_link_libraries(${PROJECT_NAME} 
                                    ${CMAKE_SOURCE_DIR}/external/glfw-3.3.7.bin.WIN64/glfw-3.3.7.bin.WIN64/lib-vc2022/glfw3.lib 
                                     ${CMAKE_SOURCE_DIR}/external/glew-2.1.0-win32/glew-2.1.0/lib/Release/x64/glew32.lib
                                     ${CMAKE_SOURCE_DIR}/external/oidn-2.3.0.x64.windows/lib/OpenImageDenoise.lib
                                     ${CMAKE_SOURCE_DIR}/external/nativefiledialog/library/nfd.lib
                                     ${CMAKE_SOURCE_DIR}/external/assimp/lib/assimp-vc143-mt.lib
                                     ${CMAKE_SOURCE_DIR}/external/FusionFrameEngine/Library/FusionFrameEngine.lib
                                     ${CMAKE_SOURCE_DIR}/external/freeimage/lib/release/FreeImage.lib
                                     opengl32.lib)

elseif(UNIX)
    find_package(OpenGL REQUIRED)
    find_package(GLEW REQUIRED)
    find_package(glfw3 REQUIRED)
    find_package(assimp REQUIRED)

    target_link_libraries(${PROJECT_NAME} PRIVATE
        ${OPENGL_LIBRARIES}
        ${GLEW_LIBRARIES}
        glfw
        assimp  
    )
endif()