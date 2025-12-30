pkgdatadir = get_option('prefix') / get_option('datadir') / meson.project_name()
moduledir = pkgdatadir / 'cookie_clicker'
gnome = import('gnome')

gnome.compile_resources('cookie-clicker',
  'cookie-clicker.gresource.xml',
  gresource_bundle: true,
  install: true,
  install_dir: pkgdatadir,
)

python = import('python')

conf = configuration_data()
conf.set('PYTHON', python.find_installation('python3').full_path())
conf.set('VERSION', meson.project_version())
conf.set('localedir', get_option('prefix') / get_option('localedir'))
conf.set('pkgdatadir', pkgdatadir)

configure_file(
  input: 'cookie-clicker.in',
  output: 'cookie-clicker',
  configuration: conf,
  install: true,
  install_dir: get_option('bindir'),
  install_mode: 'rwxr-xr-x'
)

cookie_clicker_sources = [
  '__init__.py',
  'main.py',
  'window.py',
]

install_data(cookie_clicker_sources, install_dir: moduledir)
