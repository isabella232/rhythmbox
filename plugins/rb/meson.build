rb_plugin_dir = plugindir + '/rb'

rbconfig_py = configure_file(
  input: 'rbconfig.py.in',
  output: 'rbconfig.py',
  install_dir: rb_plugin_dir,
  configuration: cdata)

rb_plugin_files = [
  'Loader.py',
  'Coroutine.py',
  'URLCache.py',
  'stringmatch.py',
  'rb.py',
  'rb.plugin']

install_data(rb_plugin_files,
  install_dir: rb_plugin_dir)

if get_option('uninstalled_build')
  # This is a hack to collect all Python source files for this plugin
  # in the build tree, so uninstalled Rhythmbox can load it.
  sh = find_program('sh')
  run_command(sh, '-c', 'cp ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.py ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.plugin ${MESON_BUILD_ROOT}/${MESON_SUBDIR}/', check: true)
endif
