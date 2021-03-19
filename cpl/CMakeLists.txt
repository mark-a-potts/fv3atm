
add_library(
    cpl

    module_cplfields.F90
    module_cap_cpl.F90
)
target_link_libraries(cpl PRIVATE esmf)

set_target_properties(cpl PROPERTIES Fortran_MODULE_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/mod)
target_include_directories(cpl INTERFACE $<BUILD_INTERFACE:${CMAKE_CURRENT_BINARY_DIR}/mod>
                                            $<INSTALL_INTERFACE:mod>)
install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/mod DESTINATION ${CMAKE_INSTALL_PREFIX})
