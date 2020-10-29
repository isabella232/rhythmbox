artsearch_plugin_dir = plugindir + '/artsearch'

artsearch_plugin_files = [
  'artsearch.py',
  'songinfo.py',
  'embedded.py',
  'lastfm.py',
  'local.py',
  'musicbrainz.py',
  'oldcache.py']

install_data(artsearch_plugin_files,
  install_dir: artsearch_plugin_dir)

artsearch_plugin_descriptor = custom_target('artsearch-plugin-descriptor',
  input: 'artsearch.plugin.in',
  output: 'artsearch.plugin',
  command: [intltool_merge, '--quiet', '--desktop-style', meson.source_root() + '/po', '@INPUT@', '@OUTPUT@'],
  install: true,
  install_dir: artsearch_plugin_dir)

if get_option('uninstalled_build')
  # This is a hack to collect all Python source files for this plugin
  # in the build tree, so uninstalled Rhythmbox can load it.
  sh = find_program('sh')
  run_command(sh, '-c', 'cp ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.py ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.plugin ${MESON_BUILD_ROOT}/${MESON_SUBDIR}/', check: true)
endif
