set(fpotencia_SOURCES
    Solver.cpp
    UnfittingSolverException.cpp
    LineConstructors.cpp
    Solution.cpp
    Circuit.cpp
    Generator.cpp
    TransformerConstructors.cpp
    Graph.cpp
    Solver_NRcurrent.cpp
    Shunt.cpp
    Circuit3.cpp
    Load.cpp
    Line.cpp
    Bus.cpp
    Solver_NRpolar.cpp
    CommonFunctions.cpp
    Transformer.cpp
    ExternalGrid.cpp)

set(fpotencia_HEADERS
    Solver.h
    UnfittingSolverException.h
    Circuit3.h
    Circuit.h
    TransformerConstructors.h
    Shunt.h
    Transformer.h
    Graph.h
    Line.h
    enumaratons.h
    Load.h
    Bus.h
    fpotencia_libs.h
    Solution.h
    fpotencia.h
    ExternalGrid.h
    Solver_NRpolar.h
    LineConstructors.h
    Solver_NRcurrent.h
    CommonFunctions.h
    Generator.h)

set(fpotencia_UNSUPPORTED_SOLVERS_HEADERS
    Solver_Jacobi.h
    Solver_ZBusGS.h
    Solver_NRrect.h)

set(fpotencia_UNSUPPORTED_SOLVERS_SOURCES
    Solver_Jacobi.cpp
    Solver_ZBusGS.cpp
    Solver_NRrect.cpp)


if(${BUILD_UNSUPPORTED_SOLVERS})
    list(APPEND ${fpotencia_SOURCES} ${fpotencia_UNSUPPORTED_SOLVERS_SOURCES})
endif()


include_directories(${eigen3_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})
add_library(fpotencia ${fpotencia_SOURCES})
target_link_libraries(fpotencia
    Boost::graph)
set_property(TARGET fpotencia PROPERTY CXX_STANDARD 11)
set_property(TARGET fpotencia PROPERTY SOVERSION ${VERSION})
install(TARGETS fpotencia
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR})
install(FILES ${fpotencia_HEADERS}
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/fpotencia)
