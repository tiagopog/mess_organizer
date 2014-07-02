# TODO:
# - Don't forget to refactor the code after all is tested;
# - Separate tasks by the file type.
task default: %w(dir:organize)

namespace :dir do
  task :organize do
    Dir.glob('*').each do |file|
      file.gsub!(/[\s\W]/) { |e| "\\#{e}" }
      case file
      when /.(txt|rtf|(p(df|ptx?|ot))|csv|xlsx?|(do(c[mx]?|tx?))|mobi|epub|(key(note)?)|log|o[dtm][mt]|pages|s[tx]w|info|(x((ht)?ml|ps))|rdoc)$/i
        sh "mkdir -p stuff/docs && mv #{file} stuff/docs"
      when /.((a(da|sm))|bat|(c(md|pp|s)?)|d|erb|(h(aml|tml)?)|slim|go|js|lua|(m(rc)?)|php\??|p[lmy][co]?|r[bu]|sh|tcl|vbs?|[s]?[ac]ss|coffee|rake|java|json|yml|((my|postgres)?sql(ite3)?))$/i
        sh "mkdir -p stuff/code && mv #{file} stuff/code"
      when /.(([ab]([bdm]f|fm))|fon|[ot]tf|ttc|woff|eot)$/i
        sh "mkdir -p stuff/fonts && mv #{file} stuff/fonts"
      when /.srt$/i
        sh "mkdir -p stuff/subtitles && mv #{file} stuff/subtitles"
      when /.torrent$/i
        sh "mkdir -p stuff/torrents && mv #{file} stuff/torrents"
      when /.([rt]ar|tbz|zip|gz|bz2)$/i
        sh "mkdir -p stuff/zips && mv #{file} stuff/zips"
      when /.(jpe?g|(p(ng|sd))|[tg]if|ico|bmp|svg)$/i
        sh "mkdir -p stuff/images && mv #{file} stuff/images"
      when /.((a(ac|lac|mr|trac))|(m(p[3c]|4a|4p|mf|sv))|mod|ogg|vox|(w(av|ma)))$/i
        sh "mkdir -p stuff/music && mv #{file} stuff/music"
      when /.(aff|3gp|avi|fl[va]|mkv|mpe?[ge]|mp4|rm|wmv)$/i
        sh "mkdir -p stuff/videos && mv #{file} stuff/videos"
      when /.(exe|dmg|app|pkg|sfx)$/i
        sh "mkdir -p stuff/apps && mv #{file} stuff/apps"
      else
        sh "mkdir -p stuff/misc && mv #{file} stuff/misc" unless file =~ /Rakefile|stuff/
      end
    end
  end
end
