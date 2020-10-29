webremote_plugin_dir = plugindir + '/webremote'
webremote_plugin_data_dir = plugindatadir + '/webremote'

webremote_plugin_files = [
  'webremote.py',
  'siphash.py',]

install_data(webremote_plugin_files,
  install_dir: webremote_plugin_dir)

webremote_plugin_descriptor = custom_target('webremote-plugin-descriptor',
  input: 'webremote.plugin.in',
  output: 'webremote.plugin',
  command: [intltool_merge, '--quiet', '--desktop-style', meson.source_root() + '/po', '@INPUT@', '@OUTPUT@'],
  install: true,
  install_dir: webremote_plugin_dir)

install_data([
  'css/grids-responsive-min.css',
  'css/pure-min.css',
  'css/webremote.css'],
  install_dir: webremote_plugin_data_dir + '/css')

install_data('js/webremote.js',
  install_dir: webremote_plugin_data_dir + '/js')

install_data('webremote.html',
  install_dir: webremote_plugin_data_dir)

install_data('webremote-config.ui',
  install_dir: webremote_plugin_data_dir)

if get_option('uninstalled_build')
  # This is a hack to collect all Python source files for this plugin
  # in the build tree, so uninstalled Rhythmbox can load it.
  sh = find_program('sh')
  run_command(sh, '-c', 'cp -a ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/* ${MESON_BUILD_ROOT}/${MESON_SUBDIR}/', check: true)
endif
