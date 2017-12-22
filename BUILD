licenses(['notice'])
package(default_visibility=['//visibility:public'])

fbs_copts = [
    '-Wall',
    '-Werror',
    '-Werror=shadow',
    '-Wextra',
    '-fsigned-char',
    '-pedantic',
]

fbs_linkopts = [
    '-lm',
]

cc_library(
    name = 'flatbuffers',
    srcs = [
        'src/code_generators.cpp',
        'src/idl_gen_text.cpp',
        'src/idl_parser.cpp',
        'src/reflection.cpp',
        'src/util.cpp',
    ],
    hdrs = [
        'include/flatbuffers/base.h',
        'include/flatbuffers/code_generators.h',
        'include/flatbuffers/flatbuffers.h',
        'include/flatbuffers/flatc.h',
        'include/flatbuffers/flexbuffers.h',
        'include/flatbuffers/hash.h',
        'include/flatbuffers/idl.h',
        'include/flatbuffers/minireflect.h',
        'include/flatbuffers/reflection.h',
        'include/flatbuffers/reflection_generated.h',
        'include/flatbuffers/registry.h',
        'include/flatbuffers/stl_emulation.h',
        'include/flatbuffers/util.h',
    ],
    includes = [
        'include',
    ],
)


cc_binary(
    name = 'flatc',
    srcs = [
        'grpc/src/compiler/cpp_generator.cc',
        'grpc/src/compiler/cpp_generator.h',
        'grpc/src/compiler/go_generator.cc',
        'grpc/src/compiler/go_generator.h',
        'grpc/src/compiler/java_generator.cc',
        'grpc/src/compiler/java_generator.h',
        'grpc/src/compiler/schema_interface.h',
        'grpc/src/compiler/config.h',
        'src/flatc.cpp',
        'src/flatc_main.cpp',
        'src/idl_gen_cpp.cpp',
        'src/idl_gen_fbs.cpp',
        'src/idl_gen_general.cpp',
        'src/idl_gen_go.cpp',
        'src/idl_gen_grpc.cpp',
        'src/idl_gen_js.cpp',
        'src/idl_gen_json_schema.cpp',
        'src/idl_gen_php.cpp',
        'src/idl_gen_python.cpp',
    ],
    copts = fbs_copts + [
        '-I./%s/grpc' % package_name(),
    ],
    linkopts = fbs_linkopts,
    deps = [
        ':flatbuffers',
    ],
)

cc_binary(
    name = 'flathash',
    srcs = [
        'src/flathash.cpp',
    ],
    copts = fbs_copts,
    linkopts = fbs_linkopts,
    deps = [
        ':flatbuffers',
    ],
)
