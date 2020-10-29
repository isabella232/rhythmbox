lyrics_plugin_dir = plugindir + '/lyrics'
lyrics_plugin_data_dir = plugindatadir + '/lyrics'

lyrics_plugin_files = [
  'LyricsParse.py',
  'LyricsSites.py',
  'LyricsConfigureDialog.py',
  'lyrics.py',
  'AstrawebParser.py',
  'LyricWikiParser.py',
  'WinampcnParser.py',
  'TerraParser.py',
  'DarkLyricsParser.py',
  'JlyricParser.py',
  'JetlyricsParser.py']

install_data(lyrics_plugin_files,
  install_dir: lyrics_plugin_dir)

lyrics_plugin_descriptor = custom_target('lyrics-plugin-descriptor',
  input: 'lyrics.plugin.in',
  output: 'lyrics.plugin',
  command: [intltool_merge, '--quiet', '--desktop-style', meson.source_root() + '/po', '@INPUT@', '@OUTPUT@'],
  install: true,
  install_dir: lyrics_plugin_dir)

install_data('lyrics-prefs.ui',
  install_dir: lyrics_plugin_data_dir)

if get_option('uninstalled_build')
  # This is a hack to collect all Python source files for this plugin
  # in the build tree, so uninstalled Rhythmbox can load it.
  sh = find_program('sh')
  run_command(sh, '-c', 'cp ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.py ${MESON_SOURCE_ROOT}/${MESON_SUBDIR}/*.plugin ${MESON_BUILD_ROOT}/${MESON_SUBDIR}/', check: true)
endif
