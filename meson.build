project('msdfgen', ['cpp'], default_options : ['default_library=static', 'cpp_std=c++11'])

msdfgen_sources = [
  'core/contour-combiners.cpp',
  'core/Contour.cpp',
  'core/edge-coloring.cpp',
  'core/EdgeHolder.cpp',
  'core/edge-segments.cpp',
  'core/edge-selectors.cpp',
  'core/equation-solver.cpp',
  'core/estimate-sdf-error.cpp',
  'core/msdfgen.cpp',
  'core/rasterization.cpp',
  'core/render-sdf.cpp',
  'core/save-bmp.cpp',
  'core/save-tiff.cpp',
  'core/Scanline.cpp',
  'core/Shape.cpp',
  'core/shape-description.cpp',
  'core/SignedDistance.cpp',
  'core/Vector2.cpp',
]

msdfgen_ext_sources = [
  'ext/import-font.cpp',
  'ext/import-svg.cpp',
  'ext/save-png.cpp',
  'lib/lodepng.cpp',
  'lib/tinyxml2.cpp',
]

external_includes = [
  include_directories('include'),
  include_directories('freetype/include'),
]

external_dependencies = [
  dependency('freetype2'),
]

msdfgen_lib = library('msdfgen', msdfgen_sources)
msdfgen_lib_dep = declare_dependency(link_with : [msdfgen_lib])

msdfgen_ext_lib = library(
  'msdfgen-ext',
  msdfgen_ext_sources,
  include_directories: external_includes,
  dependencies : external_dependencies)
msdfgen_ext_lib_dep = declare_dependency(link_with : [msdfgen_ext_lib], dependencies : external_dependencies)

msdfgen_exe = executable('msdfgen', 'main.cpp', dependencies : [ msdfgen_lib_dep, msdfgen_ext_lib_dep ], cpp_args : ['-DMSDFGEN_STANDALONE'] )

