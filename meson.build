project('gason', ['cpp'],
    default_options : [ 'cpp_std=c++11' ]
)

args = []
if meson.get_compiler('cpp').get_id() == 'msvc'
    args += [ '/GR-', '/EHsc-' ]
else
    args += [ '-fno-rtti', '-fno-exceptions' ]
endif
    
sources = files([
    'src/gason.cpp'
])

headers = files([
    'src/gason.h'
])

incdir = include_directories('src')

gason = static_library('gason', sources, include_directories : incdir, cpp_args : args, install : true)
gason_dep = declare_dependency(link_with : gason, include_directories : incdir)

pkg = import('pkgconfig')
pkg.generate(gason, name : 'gason', description : 'Simple & quick C++ json library')
