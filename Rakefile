desc 'Watch Sass/Bourbon files'
task :serve do
  puts "***************************************************"
  puts "* Watching Sass files. *"
  puts "***************************************************"
  sassPid = Process.spawn('bundle exec sass -r sass-globbing --watch sass:css')
  jekyllPid = Process.spawn('bundle exec jekyll serve')

  # Kills processes when you hit CTRL + C
  trap("INT") {
    [jekyllPid,sassPid].each { |pid| Process.kill(9, pid) rescue Errno::ESRCH }
    exit 0
  }

  [jekyll,sassPid].each { |pid| Process.wait(pid) }
end
