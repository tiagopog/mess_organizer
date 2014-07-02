module Support
  include Rake
  module_function

  REGEXES = {
    docs: /.(txt|rtf|(p(df|ptx?|ot))|csv|xlsx?|(do(c[mx]?|tx?))|mobi|epub|(key(note)?)|log|o[dtm][mt]|pages|s[tx]w|info|(x((ht)?ml|ps))|rdoc)$/i,
    code: /.((a(da|sm))|bat|(c(md|pp|s)?)|d|erb|(h(aml|tml)?)|slim|go|js|lua|(m(rc)?)|php\??|p[lmy][co]?|r[bu]|sh|tcl|vbs?|[s]?[ac]ss|coffee|rake|java|json|yml|((my|postgres)?sql(ite3)?))$/i,
    fonts: /.(([ab]([bdm]f|fm))|fon|[ot]tf|ttc|woff|eot)$/i,
    subtitles: /.srt$/i,
    torrents: /.torrent$/i,
    zips: /.([rt]ar|tbz|zip|gz|bz2)$/i,
    images: /.(jpe?g|(p(ng|sd))|[tg]if|ico|bmp|svg)$/i,
    music: /.((a(ac|lac|mr|trac))|(m(p[3c]|4a|4p|mf|sv))|mod|ogg|vox|(w(av|ma)))$/i,
    videos: /.(aff|3gp|avi|fl[va]|mkv|mpe?[ge]|mp4|rm|wmv)$/i,
    apps: /.(exe|dmg|app|pkg|sfx)$/i
  }

  def move(file, type)
    Rake.sh "mkdir -p stuff/#{type} && mv #{file} stuff/#{type}"
  end

  def check_files(which)
    Dir.glob('*').each do |file|
      file.gsub!(/[\s\W]/) { |e| "\\#{e}" }
      next if file =~ /Rakefile|README\\.md|stuff/ || (which != :all && !(file =~ REGEXES[which]))
      
      type = REGEXES.select { |k, v| v =~ file }.keys.first
      type = :misc if type.nil?
      
      move(file, type)
    end
  end
end

task default: %w(organize:all)

namespace :organize do
  ([:all] << Support::REGEXES.keys).flatten.each do |which|
    str = if which == :all 
      'Organize all the types of file in a given directory'
    else
      "Organize only #{which}"
    end
    
    desc str
    task which do
      Support.check_files(which)
    end
  end
end
