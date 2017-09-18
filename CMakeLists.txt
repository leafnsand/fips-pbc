if (NOT FIPS_IMPORT)
    cmake_minimum_required(VERSION 2.8)
    get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
    include("${FIPS_ROOT_DIR}/cmake/fips.cmake")
    fips_setup(PROJECT pbc)
endif()

fips_begin_lib(pbc)
    fips_dir(pbc)
    fips_files(
        src/alloc.c
        src/alloc.h
        src/array.c
        src/array.h
        src/bootstrap.c
        src/bootstrap.h
        src/context.c
        src/context.h
        src/decode.c
        src/descriptor.pbc.h
        src/map.c
        src/map.h
        src/pattern.c
        src/pattern.h
        src/proto.c
        src/proto.h
        src/register.c
        src/rmessage.c
        src/stringpool.c
        src/stringpool.h
        src/varint.c
        src/varint.h
        src/wmessage.c
    )
fips_end_lib()
if (FIPS_CLANG)
    set_target_properties(pbc PROPERTIES COMPILE_FLAGS "-Wno-sign-compare")
endif()

if (NOT FIPS_IMPORT)
    fips_finish()
endif()


