project('spdlog', 'cpp',
    default_options: [
        'buildtype=debugoptimized',
        'cpp_std=c++20',
        'cpp_rtti=false',
        'cpp_eh=none'
    ],
    version: '1.12.0'
)

compiler = meson.get_compiler('cpp')
link_deps = [ dependency('fmt') ]

incdirs = ['include']
cpp_flags = ['-DSPDLOG_COMPILED_LIB', '-DSPDLOG_FMT_EXTERNAL', '-DSPDLOG_NO_EXCEPTIONS']

sources = [
  'src/async.cpp',
  'src/bundled_fmtlib_format.cpp',
  'src/cfg.cpp',
  'src/color_sinks.cpp',
  'src/file_sinks.cpp',
  'src/spdlog.cpp',
  'src/stdout_sinks.cpp',
]

incdirs = include_directories(incdirs)

spdlog = library(
    'spdlog',
    sources,
    cpp_args: cpp_flags,
    include_directories: incdirs,
    dependencies: link_deps,
)
spdlog_dep = declare_dependency(
    compile_args: cpp_flags,
    include_directories: incdirs,
    dependencies: link_deps,
    link_with: spdlog,
    version: meson.project_version()
)

meson.override_dependency('spdlog', spdlog_dep)

# vim: set ts=4 sts=4 sw=4 et:
