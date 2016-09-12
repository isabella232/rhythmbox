listenbrainz_plugin_dir = plugindir + '/listenbrainz'

listenbrainz_plugin_files = [
  'client.py',
  'listenbrainz.py',
  'queue.py',
  'settings.py',
  'settings.ui',
]

install_data(listenbrainz_plugin_files,
  install_dir: listenbrainz_plugin_dir)

listenbrainz_plugin_descriptor = custom_target('listenbrainz-plugin-descriptor',
  input: 'listenbrainz.plugin.in',
  output: 'listenbrainz.plugin',
  command: [intltool_merge, '--quiet', '--desktop-style', meson.source_root() + '/po', '@INPUT@', '@OUTPUT@'],
  install: true,
  install_dir: listenbrainz_plugin_dir)
