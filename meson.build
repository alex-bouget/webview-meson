# use the base of meson build from https://github.com/webview/webview/pull/699
project('webview',
    ['c', 'cpp'],
    version: '0.10.0',
    license: 'MIT',
)

compiler_c = meson.get_compiler('c')
compiler_cpp = meson.get_compiler('cpp')

# platform specific dependenies
webview_dependencies = []

host_os = host_machine.system().to_lower()

if host_os.contains('linux') # linux os
    webview_dependencies += dependency('gtk+-3.0', version: '>= 3.24')
    webview_dependencies += dependency('webkit2gtk-4.0', version: '>= 2.0')
elif host_os.contains('darwin') or host_os.contains('machten') or host_os.contains('rhapsody')
    # TODO: add macos dependencies
elif host_os.contains('windows')
    # TODO: add windows dependencies
else
    error('Unsupported platform ' + host_os)
endif

sources_webview = [
    'webview.h'
]

libwebview = library(
    'webview',
    sources_webview,
    dependencies: webview_dependencies,
    install: true,
)

libwebview_dep = declare_dependency(
    link_with: libwebview,
    dependencies: webview_dependencies,
    include_directories: [include_directories('.')]
)