rbzeitgeist_plugin_dir = plugindir + '/rbzeitgeist'

rbzeitgeist_plugin_files = [
  'rbzeitgeist.py']

install_data(rbzeitgeist_plugin_files,
  install_dir: rbzeitgeist_plugin_dir)

rbzeitgeist_plugin_descriptor = custom_target('rbzeitgeist-plugin-descriptor',
  input: 'rbzeitgeist.plugin.in',
  output: 'rbzeitgeist.plugin',
  command: [intltool_merge, '--quiet', '--desktop-style', meson.source_root() + '/po', '@INPUT@', '@OUTPUT@'],
  install: true,
  install_dir: rbzeitgeist_plugin_dir)

if get_option('uninstalled_build')
  # This is a hack to collect all Python source files for this plugin
  # in the build tree, so uninstalled Rhythmbox can load it.
  sh = find_program('sh')
  run_command(sh, '-c', 'cp ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.py ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.plugin ${MESON_BUILD_ROOT}/${MESON_SUBDIR}/', check: true)
endif
