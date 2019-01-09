file(GLOB ALL_FILE_PATH ./*)
message(${ALL_FILE_PATH})
SET(ALL_SRC_DIR ${CMAKE_CURRENT_SOURCE_DIR})
foreach(SRC_DIR ${ALL_FILE_PATH})
    #message(${SRC_DIR})
    IF (IS_DIRECTORY ${SRC_DIR})
        file(RELATIVE_PATH t_DIR ${ALL_SRC_DIR} ${SRC_DIR})
        message(${SRC_DIR})
        message(${t_DIR})
        file(GLOB_RECURSE ALL_C ${SRC_DIR}/*.c)
        file(GLOB_RECURSE ALL_CPP ${SRC_DIR}/*.cpp)
        SET(SRC_LIST ${ALL_C} ${ALL_CPP})
        add_library(${t_DIR} ${SRC_LIST})
        #add_subdirectory(${SRC_DIR} bin/${t_DIR})
    ENDIF(IS_DIRECTORY ${SRC_DIR})
endforeach(SRC_DIR)
#add_subdirectory(${ALL_FILE_PATH})

link_directories(${PROJECT_SOURCE_DIR}/lib)
#Evaluator
aux_source_directory(./Evaluator SRC_LIST_EVA)
add_executable(Evaluator ${SRC_LIST_EVA}) 
target_link_libraries(Evaluator appl)
#Simulator
aux_source_directory(./Simulator SRC_LIST_SIM)
add_executable(Simulator ${SRC_LIST_SIM}) 
target_link_libraries(Simulator appl)
#OfflineSolver
aux_source_directory(./OfflineSolver SRC_LIST_OFF)
add_executable(OfflineSolver ${SRC_LIST_OFF}) 
target_link_libraries(OfflineSolver appl)
#PolicyGraph
aux_source_directory(./PolicyGraph SRC_LIST_POL)
add_executable(PolicyGraph ${SRC_LIST_POL}) 
target_link_libraries(PolicyGraph appl)
#PomdpConvertor
aux_source_directory(./PomdpConvertor SRC_LIST_POM)
add_executable(PomdpConvertor ${SRC_LIST_POM}) 
target_link_libraries(PomdpConvertor appl)





