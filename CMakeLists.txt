cmake_minimum_required(VERSION 3.28)
project(prg-demo CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Avertissements du cours
if(MSVC)
    add_compile_options(/W4)
else()
    add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Un exécutable par fichier demos/*.cpp : ajouter un fichier suffit,
# CLion propose la cible correspondante dans la liste de lancement.
file(GLOB DEMO_SOURCES CONFIGURE_DEPENDS demos/*.cpp)
foreach(src ${DEMO_SOURCES})
    get_filename_component(name ${src} NAME_WE)
    add_executable(${name} ${src})
endforeach()
