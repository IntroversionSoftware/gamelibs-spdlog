project('spdlog', 'cpp',
    default_options: [
        'buildtype=debugoptimized',
        'cpp_std=c++2a',
        'cpp_rtti=false',
        'cpp_eh=none'
    ]
)

compiler = meson.get_compiler('cpp')
link_deps = [ dependency('fmt') ]

incdirs = ['include']
cflags = ['-DSPDLOG_COMPILED_LIB', '-DSPDLOG_FMT_EXTERNAL', '-DSPDLOG_NO_EXCEPTIONS']

sources = [
  'src/async.cpp',
  'src/cfg.cpp',
  'src/color_sinks.cpp',
  'src/file_sinks.cpp',
  'src/fmt.cpp',
  'src/spdlog.cpp',
  'src/stdout_sinks.cpp',
]

incdirs = include_directories(incdirs)

spdlog = static_library(
    'spdlog',
    sources,
    cpp_args: cflags,
    include_directories: incdirs,
    dependencies: link_deps,
)
spdlog_dep = declare_dependency(
    include_directories: incdirs,
    dependencies: link_deps,
    link_with: spdlog,
    version: meson.project_version()
)

meson.override_dependency('spdlog', spdlog_dep)

# vim: set ts=4 sts=4 sw=4 et:
