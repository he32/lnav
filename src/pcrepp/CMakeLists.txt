add_library(pcrepp STATIC
        ../config.h.in
        pcre2pp.hh
        pcre2pp.cc)

target_include_directories(pcrepp PUBLIC . .. ../third-party/scnlib/include
        ${CMAKE_CURRENT_BINARY_DIR}/..)
target_link_libraries(pcrepp cppfmt pcre::libpcre pcre2::pcre2)

add_executable(test_pcre2pp test_pcre2pp.cc)
target_include_directories(
        test_pcre2pp
        PUBLIC
        ../third-party/doctest-root)
target_link_libraries(test_pcre2pp pcrepp)
add_test(NAME test_pcre2pp COMMAND test_pcre2pp)
