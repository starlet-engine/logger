project('starlet-logger', 'cpp',
  version : '1.0.0',
  meson_version : '>=1.1',
  default_options : ['cpp_std=c++17']
)

inc = include_directories('inc')

sources = files(
  'src/logger.cpp'
)

starlet_logger_lib = library('starlet_logger', sources, 
  include_directories : inc
)

starlet_logger_dep = declare_dependency(
  link_with : starlet_logger_lib,
  include_directories : inc
)

if get_option('build_tests')
  gtest_dep = dependency('gtest_main',
    fallback : ['gtest', 'gtest_main_dep']
  )
  subdir('tests')
endif
