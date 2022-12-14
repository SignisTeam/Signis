configure_file(
  input: 'signis.in',
  output: 'signis',
  configuration: conf,
  install_dir: get_option('bindir')
)

configure_file(
  input: 'signis.in',
  output: 'local-signis',
  configuration: local_conf
)

configure_file(
  input: 'constants.py.in',
  output: 'constants.py',
  configuration: configuration_data({
    'APP_ID': APPLICATION_ID,
    'RELEASE_VER': meson.project_version(),
    'VERSION': meson.project_version() + VERSION_SUFFIX,
    'BUILD_TYPE': get_option('buildtype'),
    'PROJECT_URL': PROJECT_URL,
    'BUGTRACKER_URL': BUGTRACKER_URL,
    'HELP_URL': HELP_URL,
    'TRANSLATE_URL': TRANSLATE_URL,
    'PKGDATA_DIR': PKGDATA_DIR,
  }),
  install: true,
  install_dir: PY_INSTALLDIR.get_install_dir() / 'signis',
)

launcher = join_paths(meson.project_build_root(), 'signis', 'local-' + meson.project_name())

run_target('run',
  command: [launcher]
)

# Install sources
signis_sources = [
  '__init__.py',
  'main.py',
  'window.py',
]

PY_INSTALLDIR.install_sources(signis_sources, subdir: 'signis')