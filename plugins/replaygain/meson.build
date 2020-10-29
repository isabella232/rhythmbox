replaygain_plugin_dir = plugindir + '/replaygain'
replaygain_plugin_data_dir = plugindatadir + '/replaygain'

replaygain_plugin_files = [
  'replaygain.py',
  'player.py',
  'config.py']

install_data(replaygain_plugin_files,
  install_dir: replaygain_plugin_dir)

replaygain_plugin_descriptor = custom_target('replaygain-plugin-descriptor',
  input: 'replaygain.plugin.in',
  output: 'replaygain.plugin',
  command: [intltool_merge, '--quiet', '--desktop-style', meson.source_root() + '/po', '@INPUT@', '@OUTPUT@'],
  install: true,
  install_dir: replaygain_plugin_dir)

install_data('replaygain-prefs.ui',
  install_dir: replaygain_plugin_data_dir)

if get_option('uninstalled_build')
  # This is a hack to collect all Python source files for this plugin
  # in the build tree, so uninstalled Rhythmbox can load it.
  sh = find_program('sh')
  run_command(sh, '-c', 'cp ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.py ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.ui ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.plugin ${MESON_BUILD_ROOT}/${MESON_SUBDIR}/', check: true)
endif
