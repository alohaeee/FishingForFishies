cmake_minimum_required(VERSION 3.16)

project(FishingForFishies
        DESCRIPTION "C++ game from scratch"
        HOMEPAGE_URL "https://github.com/alohaeee/FishingForFishies"
        LANGUAGES CXX)


file(GLOB FFF_SOURCE_FILES
        "src/*.cpp"
        )
add_executable(FishingForFishies ${FFF_SOURCE_FILES})

target_include_directories(FishingForFishies PUBLIC include)



find_package(SDL2 CONFIG REQUIRED)
target_link_libraries(FishingForFishies
        PUBLIC
        SDL2::SDL2
        SDL2::SDL2main
        )

find_package(sdl2-mixer CONFIG REQUIRED)
target_link_libraries(FishingForFishies PUBLIC SDL2::SDL2_mixer)

find_package(sdl2-image CONFIG REQUIRED)
target_link_libraries(FishingForFishies PUBLIC SDL2::SDL2_image)

find_package(sdl2-ttf CONFIG REQUIRED)
target_link_libraries(FishingForFishies PRIVATE SDL2::SDL2_ttf)

configure_file("${CMAKE_CURRENT_SOURCE_DIR}/ss22.png" "${CMAKE_CURRENT_BINARY_DIR}/ss22.png" COPYONLY)
configure_file("${CMAKE_CURRENT_SOURCE_DIR}/inf/score_table.txt" "${CMAKE_CURRENT_BINARY_DIR}/inf/score_table.txt" COPYONLY)
file(COPY "${CMAKE_CURRENT_SOURCE_DIR}/assets" DESTINATION "${CMAKE_CURRENT_BINARY_DIR}")


