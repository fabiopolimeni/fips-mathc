if (NOT FIPS_IMPORT)
    cmake_minimum_required(VERSION 2.8)
    get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
    include("${FIPS_ROOT_DIR}/cmake/fips.cmake")
    fips_setup()
    fips_project(fips-mathc)
endif()

fips_begin_lib(mathc)

    include_directories(. mathc)
    add_definitions(
        -DMATHC_NO_POINTER_STRUCT_FUNCTIONS
        -DMATHC_NO_STRUCT_FUNCTIONS)
        
    fips_dir(mathc GROUP .)
    fips_files(mathc.h mathc.c)

fips_end_lib()

if (NOT FIPS_IMPORT)
    fips_finish()
endif()