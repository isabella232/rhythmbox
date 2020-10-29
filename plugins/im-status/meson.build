im_status_plugin_dir = plugindir + '/im-status'

im_status_plugin_files = [
  'im-status.py']

install_data(im_status_plugin_files,
  install_dir: im_status_plugin_dir)

im_status_plugin_descriptor = custom_target('im-status-plugin-descriptor',
  input: 'im-status.plugin.in',
  output: 'im-status.plugin',
  command: [intltool_merge, '--quiet', '--desktop-style', meson.source_root() + '/po', '@INPUT@', '@OUTPUT@'],
  install: true,
  install_dir: im_status_plugin_dir)

if get_option('uninstalled_build')
  # This is a hack to collect all Python source files for this plugin
  # in the build tree, so uninstalled Rhythmbox can load it.
  sh = find_program('sh')
  run_command(sh, '-c', 'cp ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.py ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.plugin ${MESON_BUILD_ROOT}/${MESON_SUBDIR}/', check: true)
endif
