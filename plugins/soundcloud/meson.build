soundcloud_plugin_dir = plugindir + '/soundcloud'
soundcloud_plugin_data_dir = plugindatadir + '/soundcloud'

soundcloud_plugin_files = [
  'soundcloud.py']

install_data(soundcloud_plugin_files,
  install_dir: soundcloud_plugin_dir)

soundcloud_plugin_descriptor = custom_target('soundcloud-plugin-descriptor',
  input: 'soundcloud.plugin.in',
  output: 'soundcloud.plugin',
  command: [intltool_merge, '--quiet', '--desktop-style', meson.source_root() + '/po', '@INPUT@', '@OUTPUT@'],
  install: true,
  install_dir: soundcloud_plugin_dir)

install_data(['soundcloud.ui', 'powered-by-soundcloud.png'],
  install_dir: soundcloud_plugin_data_dir)

install_data(['icons/hicolor/scalable/places/soundcloud-symbolic.svg'],
  install_dir: soundcloud_plugin_data_dir + '/icons/hicolor/scalable/places')

if get_option('uninstalled_build')
  # This is a hack to collect all Python source files for this plugin
  # in the build tree, so uninstalled Rhythmbox can load it.
  sh = find_program('sh')
  run_command(sh, '-c', 'cp ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.py ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.ui ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.plugin ${MESON_BUILD_ROOT}/${MESON_SUBDIR}/', check: true)
endif
